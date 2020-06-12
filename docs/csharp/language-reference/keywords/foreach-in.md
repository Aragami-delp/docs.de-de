---
title: foreach-Anweisung in C#
ms.date: 06/03/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 1645a246c9feee2a92c0d4e4bbeda47f0afde7d9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401887"
---
# <a name="foreach-in-c-reference"></a>foreach, in (C#-Referenz)

Die Anweisung `foreach` führt eine Anweisung oder einen Block von Anweisungen für jedes Element in einer Instanz des Typs aus, der die Schnittstelle <xref:System.Collections.IEnumerable?displayProperty=nameWithType> oder <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> implementiert. Die Anweisung `foreach` ist nicht auf diese Typen beschränkt und kann auf eine Instanz eines beliebigen Typs angewendet werden, der die folgenden Bedingungen erfüllt:

- Er weist die öffentliche parameterlose Methode `GetEnumerator` auf, deren Rückgabetyp entweder Klasse, Struktur oder Schnittstellentyp ist.
- Der Rückgabetyp der Methode `GetEnumerator` weist die öffentliche Eigenschaft `Current` und die öffentliche parameterlose Methode `MoveNext` auf, deren Rückgabetyp <xref:System.Boolean> ist.

In den meisten Fällen iteriert `foreach` einen `IEnumerable<T>`-Ausdruck, bei dem jedes Element vom Typ `T` ist. Allerdings können die Elemente einen beliebigen Typ aufweisen, der eine implizite oder explizite Konvertierung vom Typ der `Current`-Eigenschaft aufweist. Wenn die `Current`-Eigenschaft `SomeType` zurückgibt, kann der Typ der Elemente wie folgt lauten:

- beliebige Basisklasse von `SomeType`
- beliebige von `SomeType` implementierte Schnittstelle

Wenn `SomeType` eine `class` oder `interface` und nicht `sealed` ist, kann der Typ der Elemente außerdem Folgendes enthalten:

- einen beliebigen von `SomeType` abgeleiteten Typ
- eine beliebige Schnittstelle Hier ist jede beliebige Schnittstelle zulässig, da jede Schnittstelle von einer Klasse implementiert werden kann, die von `SomeType` abgeleitet oder implementiert wurde.

Sie können die Iterationsvariable mit einem beliebigen Typ deklarieren, der mit den vorangehenden Regeln übereinstimmt. Wenn für die Konvertierung von `SomeType` in den Typ der Iterationsvariablen eine explizite Umwandlung erforderlich ist, kann dieser Vorgang eine <xref:System.InvalidCastException>-Klasse auslösen, wenn die Konvertierung fehlschlägt.

Ab C# 7.3 können Sie die Iterationsvariable mit den Modifizierern `ref` oder `ref readonly` deklarieren, wenn die `Current`-Eigenschaft des Enumerators einen [Verweisrückgabewert](ref.md#reference-return-values) (`ref T`, wobei `T` dem Typ des Auflistungselements entspricht) zurückgibt.

Ab C# 8.0 kann der `await`-Operator auf die `foreach`-Anweisung angewendet werden, wenn der Auflistungstyp die <xref:System.Collections.Generic.IAsyncEnumerable%601>-Schnittstelle implementiert. Jede Iteration der Schleife kann unterbrochen werden, während das nächste Element asynchron abgerufen wird. Standardmäßig werden Streamelemente im erfassten Kontext verarbeitet. Wenn Sie die Erfassung des Kontexts deaktivieren möchten, verwenden Sie die Erweiterungsmethode <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType>. Weitere Informationen über Synchronisierungskontexte und die Erfassung des aktuellen Kontexts finden Sie im Artikel über das [Verwenden des aufgabenbasierten asynchronen Musters](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

Sie können die Schleife an jedem Punkt im `foreach`-Anweisungsblock mit der Anweisung [break](break.md) unterbrechen oder mit der Anweisung [continue](continue.md) direkt zum nächsten Durchlauf der Schleife springen. Sie können eine `foreach`-Schleife auch mit den Anweisungen [goto](goto.md), [return](return.md) oder [throw](throw.md) beenden.

Wenn die `foreach`-Anweisung auf `null` angewendet wird, wird <xref:System.NullReferenceException> ausgelöst. Falls die Quellsammlung der `foreach`-Anweisung leer ist, wird der Text der `foreach`-Schleife nicht ausgeführt und übersprungen.

## <a name="examples"></a>Beispiele

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Das folgende Beispiel zeigt die Syntax der Anweisung `foreach` mit einer Instanz des Typs <xref:System.Collections.Generic.List%601>, der die Schnittstelle <xref:System.Collections.Generic.IEnumerable%601> implementiert:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

Im nächste Beispiel wird die Anweisung `foreach` mit einer Instanz des Typs <xref:System.Span%601?displayProperty=nameWithType> verwendet, der keine Schnittstellen implementiert:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

Im folgenden Beispiel wird eine `ref`-Iterationsvariable verwendet, um die Werte der Elemente in einem stackalloc-Array festzulegen. Die Version `ref readonly` durchläuft die Auflistung, um alle Werte auszugeben. Die `readonly`-Deklaration verwendet eine implizite lokale Variablendeklaration. Implizite Variablendeklarationen können wie explizit typisierte Variablendeklarationen mit `ref`- oder `ref readonly`-Deklarationen verwendet werden.

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

Das folgende Beispiel verwendet `await foreach`, um eine Auflistung zu durchlaufen, die jedes Element asynchron generiert:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach"  :::

## <a name="c-language-specification"></a>C#-Sprachspezifikation

Weitere Informationen finden Sie im Abschnitt [Die foreach-Anweisung](~/_csharplang/spec/statements.md#the-foreach-statement) der [C#-Sprachspezifikation](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Siehe auch

- [C#-Referenz](../index.md)
- [C#-Programmierhandbuch](../../programming-guide/index.md)
- [C#-Schlüsselwörter](index.md)
- [Verwenden von foreach mit Arrays](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [for-Anweisung](for.md)
