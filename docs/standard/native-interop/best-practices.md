---
title: 'Bewährte Methoden für native Interoperabilität: .NET'
description: Erfahren Sie mehr über bewährte Methoden für die Einrichtung von Schnittstellen mit nativen Komponenten in .NET.
ms.date: 01/18/2019
ms.openlocfilehash: e5d96471e796dca712d25d2d9e2609508180d83f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391220"
---
# <a name="native-interoperability-best-practices"></a>Bewährte Methoden für native Interoperabilität

.NET bietet verschiedene Möglichkeiten zum Anpassen Ihres Codes für die native Interoperabilität. Dieser Artikel bietet einen Leitfaden, den die .NET-Teams von Microsoft in Bezug auf die native Interoperabilität befolgen.

## <a name="general-guidance"></a>Allgemeine Anleitung

Die Anleitungen in diesem Abschnitt gelten für alle Interoperabilitätsszenarien.

- ✔️ VERWENDEN Sie die gleichen Benennungen und die gleiche Groß- und Kleinschreibung für Ihre Methoden und Parameter wie die native Methode, die Sie aufrufen möchten.
- ✔️ ERWÄGEN Sie die Verwendung der gleichen Benennungen und der gleichen Groß- und Kleinschreibung für Werte von Konstanten.
- ✔️ VERWENDEN Sie .NET-Typen, die dem nativen Typ am ähnlichsten sind. Wenn z.B. der native Typ in C# `unsigned int` ist, verwenden Sie `uint`.
- ✔️ VERWENDEN Sie nur `[In]`- und `[Out]`-Attribute, wenn sich das gewünschte Verhalten vom Standardverhalten unterscheidet.
- ✔️ ERWÄGEN Sie die Verwendung von <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType>, um Ihre nativen Arraypuffer in einem Pool zusammenzufassen.
- ✔️ ERWÄGEN Sie eine Umschließung Ihrer P/Invoke-Deklarationen in einer Klasse mit dem gleichen Namen und der gleichen Groß- und Kleinschreibung wie in Ihrer nativen Bibliothek.
  - Damit können Ihre `[DllImport]`-Attribute das C#-Sprachfeature `nameof` verwenden, um den Namen der nativen Bibliothek zu übergeben, und so sicherstellen, dass der Name der nativen Bibliothek nicht falsch geschrieben wurde.

## <a name="dllimport-attribute-settings"></a>Attributeinstellungen für „DllImport“

| Einstellung | Standard | Empfehlung | Details |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  Behalten Sie den Standardwert bei.  | Wenn diese Einstellung explizit auf „false“ festgelegt wird, werden fehlerhafte HRESULT-Rückgabewerte zu Ausnahmen umgewandelt (und der Rückgabewert in der Definition wird dadurch NULL).|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | Hängt von der API ab.  | Legen Sie diese Einstellung auf „true“ fest, wenn die API „GetLastError“ verwendet, und verwenden Sie „Marshal.GetLastWin32Error“, um den Wert abzurufen. Wenn die API eine Bedingung festlegt, die besagt, dass ein Fehler vorliegt, rufen Sie den Fehler ab, bevor Sie weitere Aufrufe senden, um ein versehentliches Überschreiben zu verhindern.|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | `CharSet.None` – Fallback auf das Verhalten `CharSet.Ansi`.  | Verwenden Sie explizit `CharSet.Unicode` oder `CharSet.Ansi`, wenn in der Definition Zeichenfolgen oder Zeichen vorhanden sind. | Damit wird das Marshallingverhalten von Zeichenfolgen angegeben und festgelegt, was `ExactSpelling` bei `false` ausführt. Beachten Sie, dass `CharSet.Ansi` tatsächlich UTF8 oder Unix ist. _In den meisten Fällen_ verwendet Windows Unicode, Unix verwendet UTF8. Weitere Informationen finden Sie in der [Dokumentation zu Zeichensätzen](./charset.md). |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | Legen Sie diesen Wert auf „true“ fest, um einen leichten Leistungsvorteil zu erzielen, da die Runtime nicht nach alternativen Funktionsnamen mit dem Suffix „A“ oder „W“ sucht, je nach Wert der Einstellung von `CharSet` („A“ für `CharSet.Ansi` und „W“ für `CharSet.Unicode`). |

## <a name="string-parameters"></a>Zeichenfolgenparameter

Wenn es sich um einen Unicode-Zeichensatz handelt oder das Argument explizit als `[MarshalAs(UnmanagedType.LPWSTR)]` gekennzeichnet ist _und_ die Zeichenfolge per Wert (nicht als `ref` oder `out`) übergeben wird, wird die Zeichenfolge angeheftet und vom nativen Code direkt verwendet (nicht kopiert).

Denken Sie daran, `[DllImport]` als `Charset.Unicode` zu kennzeichnen, es sei denn, Sie möchten explizit, dass Ihre Zeichenfolgen als ANSI verarbeitet werden.

❌ VERWENDEN SIE KEINE `[Out] string`-Parameter. Zeichenfolgenparameter, die per Wert mit dem `[Out]`-Attribut übergeben werden, können die Runtime destabilisieren, wenn die Zeichenfolge internalisiert ist. Weitere Informationen zum Internalisieren von Zeichenfolgen finden Sie in der Dokumentation zu <xref:System.String.Intern%2A?displayProperty=nameWithType>.

❌ VERMEIDEN Sie `StringBuilder`-Parameter. `StringBuilder`Marshalling erzeugt *immer* eine native Pufferkopie. Dies kann extrem ineffizient sein. Sehen Sie sich das folgende typische Szenario an, in dem eine Windows-API aufgerufen wird, die eine Zeichenfolge akzeptiert:

1. Erstellen Sie einen StringBuilder mit der gewünschten Kapazität (ordnet die verwaltete Kapazität zu) **{1}**
2. Aufrufen
   1. Ordnet einen nativen Puffer zu **{2}**
   2. Kopiert den Inhalt im Fall von `[In]` _(Standard für `StringBuilder`-Parameter)_
   3. Kopiert den nativen Puffer in ein neu zugeordnetes verwaltetes Array im Fall von `[Out]` **{3}** _(ebenfalls Standard für `StringBuilder`)_
3. `ToString()` ordnet ein weiteres verwaltetes Array zu **{4}**

Damit haben wir *{4}* Zuordnungen, um eine Zeichenfolge aus dem nativen Code abzurufen. Die beste Möglichkeit, um dies zu beschränken, besteht darin, den `StringBuilder` in einem weiteren Aufruf wiederzuverwenden, damit wird aber dennoch nur *1* Zuordnung eingespart. Es ist viel besser, einen Zeichenpuffer aus dem `ArrayPool` zu verwenden und zwischenzuspeichern – damit benötigen Sie in nachfolgenden Aufrufen nur die Zuordnung für `ToString()`.

Ein weiteres Problem bei `StringBuilder` ist, dass immer der Rückgabepuffer bis zum ersten NULL-Zeichen zurückkopiert wird. Wenn die zurückgegebene Zeichenfolge nicht beendet oder mit einem doppelten NULL-Zeichen beendet wird, ist „P/Invoke“ bestenfalls falsch.

Wenn Sie `StringBuilder`*tatsächlich* verwenden, besteht eine weitere Besonderheit darin, dass die Kapazität **kein** verborgenes NULL-Zeichen umfasst, das bei der Interoperabilität immer berücksichtigt wird. Das wird häufig falsch gemacht, da die meisten APIs die Größe des Puffers *einschließlich* des NULL-Zeichens erwarten. Dies kann zu unnötigen bzw. verschwendeten Zuordnungen führen. Darüber hinaus verhindert diese Besonderheit, dass die Runtime das Marshalling von `StringBuilder` optimiert, um die Erstellung von Kopien zu minimieren.

✔️ ERWÄGEN Sie die Verwendung von `char[]`s aus einem `ArrayPool`.

Weitere Informationen zum Marshalling von Zeichenfolgen finden Sie unter [Standardmäßiges Marshalling für Zeichenfolgen](../../framework/interop/default-marshaling-for-strings.md) und [Anpassen des Zeichenfolgenmarshallings](customize-parameter-marshaling.md#customizing-string-parameters).

> __Windows-spezifisch:__ Bei `[Out]`-Zeichenfolgen verwendet die CLR (Common Language Runtime) standardmäßig `CoTaskMemFree`, um Zeichenfolgen freizugeben, oder `SysStringFree` bei Zeichenfolgen, die als `UnmanagedType.BSTR` gekennzeichnet sind.
> **Bei den meisten APIs mit Puffer für Ausgabezeichenfolgen gilt Folgendes**: Die übergebene Zeichenanzahl muss das NULL-Zeichen enthalten. Wenn der zurückgegebene Wert kleiner ist als die Zeichenanzahl, ist der Aufruf erfolgreich und der Wert ist die Anzahl der Zeichen *ohne* das nachgestellte NULL-Zeichen. Andernfalls ist die Anzahl die erforderliche Größe des Puffers *einschließlich* des NULL-Zeichens.
>
> - 5 übergeben, 4 abrufen: Die Zeichenfolge ist 4 Zeichen lang und umfasst ein nachgestelltes NULL-Zeichen.
> - 5 übergeben, 6 abrufen: Die Zeichenfolge ist 5 Zeichen lang und erfordert einen Puffer mit 6 Zeichen für das NULL-Zeichen.
> [Windows-Datentypen für Zeichenfolgen](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a>Boolesche Parameter und Felder

Bei booleschen Werten passieren leicht Fehler. Standardmäßig erfolgt für einen `bool`-Wert von .NET ein Marshalling in einen `BOOL`-Wert in Windows. Dort handelt es sich um einen 4 Byte langen Wert. Die Typen `_Bool` und `bool` in C und C++ sind jedoch *Einzelbytewerte*. Dies kann zu Bugs führen, die sich nur sehr schwer auffinden lassen, da der halbe Rückgabewert verworfen wird, sich das Ergebnis aber nur *möglicherweise* ändert. Weitere Informationen zum Marshalling von `bool`-Werten aus .NET in `bool`-Typen in C oder C++ finden Sie in der Dokumentation zum [Anpassen des Marshallings von booleschen Feldern](customize-struct-marshaling.md#customizing-boolean-field-marshaling).

## <a name="guids"></a>GUIDs

GUIDs können direkt in Signaturen verwendet werden. Viele Windows-APIs akzeptieren `GUID&`-Typen wie `REFIID`. Bei der Übergabe per Verweis können diese durch `ref` oder mit dem Attribut `[MarshalAs(UnmanagedType.LPStruct)]` übergeben werden.

| GUID | By-ref-GUID |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

❌ VERWENDEN SIE NICHT `[MarshalAs(UnmanagedType.LPStruct)]` für etwas anderes als für `ref`-GUID-Parameter.

## <a name="blittable-types"></a>Für Blitting geeignete Typen

Für Blitting geeignete Typen sind Typen, die in verwaltetem und nativem Code die gleiche Darstellung auf Bitebene aufweisen. Als solche müssen sie nicht in ein anderes Format konvertiert werden, um ein Marshalling in den und aus dem nativen Code zu ermöglichen. Da dies die Leistung verbessert, sind diese Typen zu bevorzugen.

**Für Blitting geeignete Typen**:

- `byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`
- Nicht geschachtelte eindimensionale Arrays aus für Blitting geeigneten Typen (z.B. `int[]`)
- Strukturen und Klassen mit festem Layout, die für Instanzfelder nur über für Blitting geeignete Typen verfügen
  - Ein festes Layout erfordert `[StructLayout(LayoutKind.Sequential)]` oder `[StructLayout(LayoutKind.Explicit)]`
  - Strukturen sind standardmäßig `LayoutKind.Sequential`, Klassen sind `LayoutKind.Auto`

**NICHT für Blitting geeignet**:

- `bool`

**MANCHMAL für Blitting geeignet**:

- `char`, `string`

Wenn für Blitting geeignete Typen per Verweis übergeben werden, werden sie einfach vom Marshaller angeheftet, anstatt in einem temporären Puffer kopiert zu werden. (Klassen werden von Natur aus per Verweis übergeben, Strukturen werden per Verweis übergeben, wenn sie mit `ref` oder `out` verwendet werden.)

`char` ist in einem eindimensionalen Array **oder** bei Verwendung in einem Typen für Blitting geeignet, der explizit mit `[StructLayout]` mit `CharSet = CharSet.Unicode` gekennzeichnet ist.

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

`string` ist für Blitting geeignet, wenn es nicht in einem anderen Typen enthalten ist und als Argument übergeben wird, das mit `[MarshalAs(UnmanagedType.LPWStr)]` gekennzeichnet ist oder in dem `CharSet = CharSet.Unicode` für `[DllImport]` festgelegt ist.

Sie können feststellen, ob ein Typ für Blitting geeignet ist, indem Sie versuchen, ein angeheftetes `GCHandle` zu erstellen. Wenn der Typ keine Zeichenfolge ist oder nicht als für Blitting geeignet betrachtet wird, löst `GCHandle.Alloc` eine `ArgumentException` aus.

✔️ LEGEN Sie Ihre Strukturen nach Möglichkeit als für Blitting geeignet fest.

Weitere Informationen finden Sie unter:

- [Blitfähige und nicht blitfähige Typen](../../framework/interop/blittable-and-non-blittable-types.md)
- [Marshalling von Typen](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a>Beibehalten von verwalteten Objekten

`GC.KeepAlive()` stellt sicher, dass ein Objekt im Gültigkeitsbereich bleibt, bis die KeepAlive-Methode erreicht wird.

[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) ermöglicht es dem Marshaller, ein Objekt während der Dauer eines P/Invoke beizubehalten. Es kann statt `IntPtr` in Methodensignaturen verwendet werden. `SafeHandle` ersetzt diese Klasse und sollte stattdessen verwendet werden.

[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) ermöglicht das Anheften eines verwalteten Objekts und Abrufen des nativen Zeigers auf das Objekt. Das grundlegende Muster sieht folgendermaßen aus:

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

Anheften ist kein Standardvorgang für `GCHandle`. Das andere wichtige Muster sieht so aus: Ein Verweis wird über nativen Code an ein verwaltetes Objekt übergeben und, in der Regel über einen Rückruf, wieder zurückgegeben. Hier sehen Sie das Muster:

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

Denken Sie daran, dass `GCHandle` explizit freigegeben werden muss, um Arbeitsspeicherverluste zu vermeiden.

## <a name="common-windows-data-types"></a>Allgemeine Windows-Datentypen

Die folgende Liste enthält Datentypen, die in Windows-APIs häufig verwendet werden, sowie C#-Typen, die beim Aufrufen des Windows-Codes verwendet werden sollen.

Die folgenden Typen weisen trotz ihrer Namen die gleiche Größe wie 32- und 64-Bit-Typen für Windows auf.

| Breite | Windows          | C (Windows)          | C#       | Alternative                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| 32    | `BOOL`           | `int`                | `int`    | `bool`                               |
| 8     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| 8     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| 8     | `CHAR`           | `char`               | `sbyte`  |                                      |
| 8     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| 16    | `SHORT`          | `short`              | `short`  |                                      |
| 16    | `CSHORT`         | `short`              | `short`  |                                      |
| 16    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| 16    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| 16    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| 32    | `INT`            | `int`                | `int`    |                                      |
| 32    | `LONG`           | `long`               | `int`    |                                      |
| 32    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| 32    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| 64    | `QWORD`          | `long long`          | `long`   |                                      |
| 64    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| 64    | `LONGLONG`       | `long long`          | `long`   |                                      |
| 64    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| 64    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| 32    | `HRESULT`        | `long`               | `int`    |                                      |
| 32    | `NTSTATUS`       | `long`               | `int`    |                                      |

Die folgenden Typen sind Zeiger und entsprechen der Breite der Plattform. Verwenden Sie `IntPtr`/`UIntPtr` für diese.

| Signierte Zeigertypen (verwenden Sie `IntPtr`). | Nicht signierte Zeigertypen (verwenden Sie `UIntPtr`). |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

Für einen `PVOID`-Wert in Windows, der `void*` in C entspricht, kann ein Marshalling als `IntPtr` oder `UIntPtr` erfolgen. `void*` sollte jedoch nach Möglichkeit bevorzugt werden.

[Windows-Datentypen](/windows/desktop/WinProg/windows-data-types)

[Datentypbereiche](/cpp/cpp/data-type-ranges)

## <a name="structs"></a>Strukturen

Verwaltete Strukturen werden im Stapel erstellt und erst dann entfernt, wenn die Methode zurückgegeben wird. Per Definition werden sie „angeheftet“ (also von der Garbage Collection nicht verschoben). Sie können auch einfach die Adresse in unsicheren Codeblöcken verwenden, wenn der native Code den Zeiger nicht über das Ende der aktuellen Methode hinaus verwendet.

Für Blitting geeignete Strukturen sind wesentlich leistungsfähiger, da sie ganz einfach direkt von der Marshallingebene genutzt werden können. Versuchen Sie, Typen blitfähig zu machen (vermeiden Sie z.B. `bool`). Weitere Informationen finden Sie im Abschnitt [Für Blitting geeignete Typen](#blittable-types).

*Wenn* eine Struktur für Blitting geeignet ist, verwenden Sie `sizeof()` statt `Marshal.SizeOf<MyStruct>()`, um eine bessere Leistung zu erzielen. Wie oben erwähnt, können Sie überprüfen, ob der Typ für Blitting geeignet ist, indem Sie versuchen, ein angeheftetes `GCHandle` zu erstellen. Wenn der Typ keine Zeichenfolge ist oder nicht als für Blitting geeignet betrachtet wird, löst `GCHandle.Alloc` eine `ArgumentException` aus.

Zeiger auf Strukturen in Definitionen müssen entweder von `ref` übergeben werden oder `unsafe` und `*` verwenden.

✔️ PASSEN Sie die verwaltete Struktur so eng wie möglich an die Form und die Namen an, die in der offiziellen Dokumentation zur Plattform oder im Header verwendet werden.

✔️ VERWENDEN Sie `sizeof()` aus C# anstelle von `Marshal.SizeOf<MyStruct>()` für Strukturen, die für Blitting geeignet sind, um die Leistung zu verbessern.

❌ VERMEIDEN Sie die Verwendung von `System.Delegate`- oder `System.MulticastDelegate`-Feldern, um Felder für Funktionszeiger in Strukturen darzustellen.

Da <xref:System.Delegate?displayProperty=fullName> und <xref:System.MulticastDelegate?displayProperty=fullName> nicht über eine erforderliche Signatur verfügen, garantieren sie nicht, dass der übergebene Delegat der Signatur entspricht, die vom nativen Code erwartet wird. Außerdem kann in .NET Framework und .NET Core das Marshalling einer Struktur, die einen `System.Delegate` oder einen `System.MulticastDelegate` aus ihrer nativen Darstellung in ein verwaltetes Objekt enthält, die Runtime destabilisieren, wenn der Wert des Felds in der nativen Darstellung kein Funktionszeiger ist, der einen verwalteten Delegaten umschließt. In .NET 5 und höheren Versionen wird das Marshalling eines `System.Delegate`- oder `System.MulticastDelegate`-Felds aus einer nativen Darstellung in ein verwaltetes Objekt nicht unterstützt. Verwenden Sie anstelle von `System.Delegate` oder `System.MulticastDelegate` einen bestimmten Delegattyp.

### <a name="fixed-buffers"></a>Puffer fester Größe

Für ein Array wie `INT_PTR Reserved1[2]` muss ein Marshalling in zwei `IntPtr`-Felder durchgeführt werden: `Reserved1a` und `Reserved1b`. Wenn das native Array ein primitiver Typ ist, können wir das Schlüsselwort `fixed` verwenden, um es etwas übersichtlicher zu schreiben. `SYSTEM_PROCESS_INFORMATION` sieht im nativen Header beispielsweise so aus:

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

In C# können wir es folgendermaßen schreiben:

```csharp
internal unsafe struct SYSTEM_PROCESS_INFORMATION
{
    internal uint NextEntryOffset;
    internal uint NumberOfThreads;
    private fixed byte Reserved1[48];
    internal Interop.UNICODE_STRING ImageName;
    ...
}
```

Es gibt jedoch einige Besonderheiten bei festen Puffern. Bei festen Puffern aus nicht für Blitting geeigneten Typen wird das Marshalling nicht ordnungsgemäß ausgeführt, daher muss das vorhandene Array auf mehrere einzelne Felder erweitert werden. Darüber hinaus gilt für .NET Framework und .NET Core vor Version 3.0: Wenn eine Struktur, die ein festes Pufferfeld enthält, in einer nicht für Blitting geeigneten Struktur geschachtelt wird, erfolgt kein ordnungsgemäßes Marshalling des festen Pufferfelds zum nativen Code.
