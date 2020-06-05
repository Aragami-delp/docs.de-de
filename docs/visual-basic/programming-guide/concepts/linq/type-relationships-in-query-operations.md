---
title: Typbeziehungen in Abfragevorgängen
ms.date: 07/20/2015
helpviewer_keywords:
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
ms.openlocfilehash: 73a287541ddf115510bf6ab5c830eafac370cc3a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406728"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>Typbeziehungen in Abfrageoperationen (Visual Basic)

Variablen, die in LINQ-Abfrage Vorgängen (Language-Integrated Query) verwendet werden, sind stark typisiert und müssen miteinander kompatibel sein. Starke Typisierung wird in der Datenquelle, in der Abfrage selbst und in der Abfrage Ausführung verwendet. In der folgenden Abbildung sind Begriffe aufgeführt, die zum Beschreiben einer LINQ-Abfrage verwendet werden. Weitere Informationen zu den Teilen einer Abfrage finden Sie unter [grundlegende Abfrage Vorgänge (Visual Basic)](basic-query-operations.md).

![Screenshot, der eine Pseudo Code-Abfrage mit hervorgehobenen Elementen anzeigt.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)

Der Typ der Bereichs Variablen in der Abfrage muss mit dem Typ der Elemente in der Datenquelle kompatibel sein. Der Typ der Abfrage Variablen muss mit dem in der-Klausel definierten Sequence-Element kompatibel sein `Select` . Schließlich muss der Typ der Sequenz Elemente auch mit dem Typ der Schleifen Steuerungsvariablen kompatibel sein, die in der Anweisung verwendet wird `For Each` , die die Abfrage ausführt. Diese starke Typisierung vereinfacht die Identifizierung von Typfehlern zum Zeitpunkt der Kompilierung.

Mit Visual Basic wird die starke Typisierung durch Implementieren des lokalen Typrückschlusses, auch als *implizite Typisierung*bezeichnet, vereinfacht. Diese Funktion wird im vorherigen Beispiel verwendet, und Sie sehen, dass Sie in den LINQ-Beispielen und in der Dokumentation verwendet wird. In Visual Basic wird der lokale Typrückschluss einfach mithilfe einer- `Dim` Anweisung ohne eine- `As` Klausel erreicht. Im folgenden Beispiel `city` ist als Zeichenfolge stark typisiert.

[!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]

> [!NOTE]
> Der lokale Typrückschluss funktioniert nur `Option Infer` , wenn auf festgelegt ist `On` . Weitere Informationen finden Sie unter [Option Infer-Anweisung](../../../language-reference/statements/option-infer-statement.md).

Auch wenn Sie einen lokalen Typrückschluss in einer Abfrage verwenden, sind die gleichen Typbeziehungen zwischen den Variablen in der Datenquelle, der Abfrage Variablen und der Abfrage Ausführungs Schleife vorhanden. Es ist hilfreich, wenn Sie LINQ-Abfragen schreiben oder mit den Beispielen und Codebeispielen in der Dokumentation arbeiten.

Möglicherweise müssen Sie einen expliziten Typ für eine Bereichs Variable angeben, der nicht mit dem von der Datenquelle zurückgegebenen Typ identisch ist. Sie können den Typ der Bereichs Variablen angeben, indem Sie eine- `As` Klausel verwenden. Dies führt jedoch zu einem Fehler, wenn die Konvertierung eine einschränkende [Konvertierung](../../language-features/data-types/widening-and-narrowing-conversions.md) ist und `Option Strict` auf festgelegt ist `On` . Daher wird empfohlen, die Konvertierung der aus der Datenquelle abgerufenen Werte durchzuführen. Mithilfe der-Methode können Sie die Werte aus der Datenquelle in den expliziten Range-Variablentyp konvertieren <xref:System.Linq.Enumerable.Cast%2A> . Sie können auch die in der-Klausel ausgewählten Werte in `Select` einen expliziten Typ umwandeln, der sich vom Typ der Bereichs Variablen unterscheidet. Diese Punkte sind im folgenden Code dargestellt.

[!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]

## <a name="queries-that-return-entire-elements-of-the-source-data"></a>Abfragen, die ganze Elemente der Quelldaten zurückgeben

Das folgende Beispiel zeigt einen LINQ-Abfrage Vorgang, der eine Sequenz von Elementen zurückgibt, die aus den Quelldaten ausgewählt wurden. Die Quelle, `names` , enthält ein Array von Zeichen folgen, und die Abfrageausgabe ist eine Sequenz mit Zeichen folgen, die mit dem Buchstaben "M" beginnen.

[!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]

Dies entspricht dem folgenden Code, ist aber viel kürzer und einfacher zu schreiben. Die Abhängigkeit von lokalem Typrückschluss in Abfragen ist der bevorzugte Stil in Visual Basic.

[!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]

Die folgenden Beziehungen sind in beiden vorherigen Codebeispielen vorhanden, unabhängig davon, ob die Typen implizit oder explizit bestimmt werden.

1. Der Typ der Elemente in der Datenquelle, `names` , ist der Typ der Bereichs Variablen `name` in der Abfrage.

2. Der Typ des ausgewählten Objekts, `name` , bestimmt den Typ der Abfrage Variablen `mNames` . Hier `name` ist eine Zeichenfolge, sodass die Abfrage Variable in Visual Basic IEnumerable (of String) ist.

3. Die in definierte Abfrage `mNames` wird in der- `For Each` Schleife ausgeführt. Die Schleife durchläuft das Ergebnis der Ausführung der Abfrage. Da `mNames` beim Ausführen von eine Sequenz von Zeichen folgen zurückgibt, ist die Schleifen Iterations Variable, `nm` , ebenfalls eine Zeichenfolge.

## <a name="queries-that-return-one-field-from-selected-elements"></a>Abfragen, die ein Feld aus ausgewählten Elementen zurückgeben

Das folgende Beispiel zeigt einen [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] Abfrage Vorgang, der eine Sequenz mit nur einem Teil der einzelnen aus der Datenquelle ausgewählten Elemente zurückgibt. Die Abfrage nimmt eine Auflistung von `Customer` -Objekten als Datenquelle an und projiziert nur die- `Name` Eigenschaft im Ergebnis. Da der Kunden Name eine Zeichenfolge ist, erzeugt die Abfrage eine Sequenz von Zeichen folgen als Ausgabe.

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim custNames = From cust In customers
                Where cust.City = "London"
                Select cust.Name

For Each custName In custNames
    Console.WriteLine(custName)
Next
```

Die Beziehungen zwischen Variablen ähneln denen im einfacheren Beispiel.

1. Der Typ der Elemente in der Datenquelle, `customers` , ist der Typ der Bereichs Variablen `cust` in der Abfrage. In diesem Beispiel ist dieser Typ `Customer` .

2. Die- `Select` Anweisung gibt die- `Name` Eigenschaft der einzelnen- `Customer` Objekte anstelle des gesamten-Objekts zurück. Da `Name` eine Zeichenfolge ist, ist die Abfrage Variable, `custNames` , erneut IEnumerable (of String), nicht von `Customer` .

3. Da `custNames` eine Sequenz von Zeichen folgen darstellt, `For Each` muss die Iterations Variable der-Schleife `custName` eine Zeichenfolge sein.

Ohne den lokalen Typrückschluss wäre das vorherige Beispiel etwas mühsamer zu schreiben und zu verstehen, wie im folgenden Beispiel gezeigt.

```vb
' Method GetTable returns a table of Customer objects.
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()
 Dim custNames As IEnumerable(Of String) =
     From cust As Customer In customers
     Where cust.City = "London"
     Select cust.Name

 For Each custName As String In custNames
     Console.WriteLine(custName)
 Next
```

## <a name="queries-that-require-anonymous-types"></a>Abfragen, die anonyme Typen erfordern

Das folgende Beispiel zeigt eine komplexere Situation. Im vorherigen Beispiel war es unpraktisch, Typen für alle Variablen explizit anzugeben. In diesem Beispiel ist es nicht möglich. Anstatt ganze `Customer` Elemente aus der Datenquelle oder ein einzelnes Feld aus jedem Element auszuwählen, `Select` gibt die-Klausel in dieser Abfrage zwei Eigenschaften des ursprünglichen `Customer` -Objekts zurück: `Name` und `City` . Als Antwort auf die- `Select` Klausel definiert der Compiler einen anonymen Typ, der diese beiden Eigenschaften enthält. Das Ergebnis der Ausführung von `nameCityQuery` in der- `For Each` Schleife ist eine Auflistung von Instanzen des neuen anonymen Typs. Da der anonyme Typ keinen verwendbaren Namen hat, können Sie den Typ `nameCityQuery` oder nicht `custInfo` explizit angeben. Das heißt, bei einem anonymen Typ haben Sie keinen Typnamen, der anstelle von in verwendet werden kann `String` `IEnumerable(Of String)` . Weitere Informationen finden Sie unter [Anonyme Typen](../../language-features/objects-and-classes/anonymous-types.md).

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim nameCityQuery = From cust In customers
                    Where cust.City = "London"
                    Select cust.Name, cust.City

For Each custInfo In nameCityQuery
    Console.WriteLine(custInfo.Name)
Next
```

Obwohl es nicht möglich ist, Typen für alle Variablen im vorherigen Beispiel anzugeben, bleiben die Beziehungen unverändert.

1. Der Typ der Elemente in der Datenquelle ist wieder der Typ der Bereichs Variablen in der Abfrage. In diesem Beispiel `cust` ist eine Instanz von `Customer` .

2. Da die- `Select` Anweisung einen anonymen Typ erzeugt, muss die Abfrage Variable `nameCityQuery` implizit als anonymer Typ typisiert werden. Ein anonymer Typ hat keinen verwendbaren Namen und kann daher nicht explizit angegeben werden.

3. Der Typ der Iterations Variablen in der `For Each` Schleife ist der anonyme Typ, der in Schritt 2 erstellt wurde. Da der Typ keinen verwendbaren Namen hat, muss der Typ der Schleifen Iterations Variablen implizit bestimmt werden.

## <a name="see-also"></a>Weitere Informationen

- [Erste Schritte mit LINQ in Visual Basic](getting-started-with-linq.md)
- [Anonyme Typen](../../language-features/objects-and-classes/anonymous-types.md)
- [Lokaler Typrückschluss](../../language-features/variables/local-type-inference.md)
- [Einführung in LINQ in Visual Basic](../../language-features/linq/introduction-to-linq.md)
- [LINQ](../../language-features/linq/index.md)
- [Abfragen](../../../language-reference/queries/index.md)
