---
title: Integrale numerische Typen – C#-Referenz
description: Erfahren Sie mehr über den Bereich, die Speichergröße und die Verwendung für jeden integralen numerischen Typen.
ms.date: 10/22/2019
f1_keywords:
- byte
- byte_CSharpKeyword
- sbyte_CSharpKeyword
- sbyte
- short
- short_CSharpKeyword
- ushort
- ushort_CSharpKeyword
- int_CSharpKeyword
- int
- uint
- uint_CSharpKeyword
- long_CSharpKeyword
- long
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
- byte keyword [C#]
- sbyte keyword [C#]
- short keyword [C#]
- ushort keyword [C#]
- int keyword [C#]
- uint keyword [C#]
- long keyword [C#]
- ulong keyword [C#]
ms.openlocfilehash: 51ea64065ea8422e5885022105545780bc916f06
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739007"
---
# <a name="integral-numeric-types--c-reference"></a>Integrale numerische Typen (C#-Referenz)

Die *integralen numerischen Typen* stellen ganze Zahlen dar. Alle integralen numerischen Typen sind [Werttypen](value-types.md). Sie sind auch [einfache Typen](value-types.md#built-in-value-types) und können mit [Literalen](#integer-literals) initialisiert werden. Alle integralen numerischen Typen unterstützen [arithmetic](../operators/arithmetic-operators.md)-, [bitwise logical](../operators/bitwise-and-shift-operators.md)-, [comparison](../operators/comparison-operators.md)- and [equality](../operators/equality-operators.md)-Operatoren.

## <a name="characteristics-of-the-integral-types"></a>Merkmale der integralen Typen

C# unterstützt die folgenden vordefinierten integralen Typen:

|C#-Typ/Schlüsselwort|Bereich|Größe|.NET-Typ|
|----------|-----------|----------|-------------|
|`sbyte`|–128 bis 127|Ganze 8-Bit-Zahl mit Vorzeichen|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|0 bis 255|8-Bit-Ganzzahl ohne Vorzeichen|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|–32.768 bis 32.767|Ganze 16-Bit-Zahl mit Vorzeichen|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|0 bis 65.535|16-Bit-Ganzzahl ohne Vorzeichen|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|-2,147,483,648 bis 2,147,483,647|Eine 32-Bit-Ganzzahl mit Vorzeichen|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|0 bis 4.294.967.295|32-Bit Ganzzahl ohne Vorzeichen|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|-9,223,372,036,854,775,808 bis 9,223,372,036,854,775,807|64-Bit-Ganzzahl mit Vorzeichen|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|0 bis 18.446.744.073.709.551.615|64-Bit-Ganzzahl ohne Vorzeichen|<xref:System.UInt64?displayProperty=nameWithType>|

In der obigen Tabelle ist jedes C#-Typschlüsselwort aus der äußerst linken Spalte ein Alias für den entsprechenden .NET-Typ. Sie können synonym verwendet werden. In den folgenden Deklarationen werden beispielsweise Variablen des gleichen Typs deklariert:

```csharp
int a = 123;
System.Int32 b = 123;
```

Der Standardwert jedes integralen Typs ist Null (`0`). Die einzelnen integralen Typen verfügen jeweils über die Konstanten `MinValue` und `MaxValue`, die den minimalen und maximalen Wert des Typs angeben.

Verwenden Sie die <xref:System.Numerics.BigInteger?displayProperty=nameWithType>-Struktur, um eine ganze Zahl mit Vorzeichen ohne obere oder untere Grenzen darzustellen.

## <a name="integer-literals"></a>Ganzzahlenliteral

Ganzzahlenliterale können die folgenden Typen aufweisen:

- *Dezimal* : ohne Präfix
- *Hexadezimal*: mit dem Präfix `0x` oder `0X`
- *Binär*: mit dem Präfix `0b` oder `0B` (verfügbar in C# 7.0 und höher)

Der folgende Code zeigt ein Beispiel für jeden Typ:

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

Das vorherige Beispiel zeigt auch die Verwendung von `_` als *Zifferntrennzeichen*, das ab C# 7.0 unterstützt wird. Sie können das Zifferntrennzeichen mit allen Arten numerischer Literale verwenden.

Der Typ eines integralen Literals wird wie folgt durch sein Suffix bestimmt:

- Wenn das Literal kein Suffix besitzt, ist sein Typ der erste dieser Typen, in dem sein Wert dargestellt werden kann: `int`, `uint`, `long`, `ulong`.
- Wenn das Literal das Suffix `U` oder `u` aufweist, ist sein Typ der erste dieser Typen, in dem sein Wert dargestellt werden kann: `uint`, `ulong`.
- Wenn das Literal das Suffix `L` oder `l` aufweist, ist sein Typ der erste dieser Typen, in dem sein Wert dargestellt werden kann: `long`, `ulong`.

  > [!NOTE]
  > Sie können den Kleinbuchstaben `l` als Suffix verwenden. Allerdings erzeugt dies eine Compilerwarnung, weil der Buchstabe `l` leicht mit der Zahl `1` verwechselt werden kann. Verwenden Sie aus Gründen der Klarheit `L`.

- Wenn das Literal das Suffix `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU` oder `lu` aufweist, ist sein Typ `ulong`.

Wenn der von einem Integer-Literal dargestellte Wert <xref:System.UInt64.MaxValue?displayProperty=nameWithType> überschreitet, tritt der Compilerfehler [CS1021](../../misc/cs1021.md) auf.

Wenn der festgelegte Typ eines Integerliterals `int` lautet, und der vom Literal dargestellte Wert innerhalb des Bereichs des Zieltyps liegt, kann der Wert implizit in `sbyte`, `byte`, `short`, `ushort`, `uint` oder `ulong` konvertiert werden:

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

Wie das vorherige Beispiel zeigt, tritt der Compilerfehler [CS0031](../../misc/cs0031.md) auf, wenn der Wert des Literals nicht innerhalb des Bereichs des Zieltyps liegt.

Sie können auch eine Umwandlung verwenden, um den Wert, der durch ein Ganzzahlliteral dargestellt wird, in einen anderen Typ als den festgelegten Literaltyp zu konvertieren:

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a>Konvertierungen

Sie können beliebige ganzzahlige numerische Typen in beliebige andere ganzzahlige numerische Typen konvertieren. Wenn der Zieltyp alle Werte des Quelltyps speichern kann, handelt es sich um eine implizite Konvertierung. Andernfalls müssen Sie einen [Cast-Ausdruck](../operators/type-testing-and-cast.md#cast-expression) verwenden, um eine explizite Konvertierung durchzuführen. Weitere Informationen finden Sie unter [Integrierte numerische Konvertierungen (C#-Referenz)](numeric-conversions.md) (Integrierte numerische Konvertierungen).

## <a name="c-language-specification"></a>C#-Sprachspezifikation

Weitere Informationen finden Sie in den folgenden Abschnitten der [C#-Sprachspezifikation](~/_csharplang/spec/introduction.md):

- [Integrale Typen](~/_csharplang/spec/types.md#integral-types)
- [Ganzzahlenliterale](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a>Siehe auch

- [C#-Referenz](../index.md)
- [Werttypen](value-types.md)
- [Gleitkommatypen](floating-point-numeric-types.md)
- [Standardmäßige Zahlenformatzeichenfolgen](../../../standard/base-types/standard-numeric-format-strings.md)
- [Numerische Ausdrücke in .NET](../../../standard/numerics.md)
