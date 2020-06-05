---
title: 'Vorgehensweise: Abfragen von Sätzen, die bestimmte Wörter enthalten (LINQ)'
ms.date: 07/20/2015
ms.assetid: a5ae8ced-61fe-4c10-bb8a-95630e50f603
ms.openlocfilehash: ce88bf001346f90eb9b08ca1ff14afc7dcb04fa0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397959"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a><span data-ttu-id="5a3e5-102">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic) (Gewusst wie: Abfragen von Sätzen, die bestimmte Wörter enthalten (LINQ) (C#))</span><span class="sxs-lookup"><span data-stu-id="5a3e5-102">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="5a3e5-103">Dieses Beispiel zeigt, wie Sie Sätze in einer Textdatei suchen, die Übereinstimmungen für jedes Wort einer bestimmten Gruppe von Wörtern enthält.</span><span class="sxs-lookup"><span data-stu-id="5a3e5-103">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="5a3e5-104">Obwohl das Array von Suchbegriffen in diesem Beispiel hartcodiert ist, kann es auch zur Laufzeit dynamisch aufgefüllt werden.</span><span class="sxs-lookup"><span data-stu-id="5a3e5-104">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="5a3e5-105">In diesem Beispiel gibt die Abfrage die Sätze zurück, die die Wörter „Historically“ (ursprünglich), „data“ (Daten) und „integrated“ (integriert) enthalten.</span><span class="sxs-lookup"><span data-stu-id="5a3e5-105">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>

## <a name="example"></a><span data-ttu-id="5a3e5-106">Beispiel</span><span class="sxs-lookup"><span data-stu-id="5a3e5-106">Example</span></span>

```vb
Class FindSentences

    Shared Sub Main()
        Dim text As String = "Historically, the world of data and the world of objects " &
        "have not been well integrated. Programmers work in C# or Visual Basic " &
        "and also in SQL or XQuery. On the one side are concepts such as classes, " &
        "objects, fields, inheritance, and .NET Framework APIs. On the other side " &
        "are tables, columns, rows, nodes, and separate languages for dealing with " &
        "them. Data types often require translation between the two worlds; there are " &
        "different standard functions. Because the object world has no notion of query, a " &
        "query can only be represented as a string without compile-time type checking or " &
        "IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " &
        "objects in memory is often tedious and error-prone."

        ' Split the text block into an array of sentences.
        Dim sentences As String() = text.Split(New Char() {".", "?", "!"})

        ' Define the search terms. This list could also be dynamically populated at runtime
        Dim wordsToMatch As String() = {"Historically", "data", "integrated"}

        ' Find sentences that contain all the terms in the wordsToMatch array
        ' Note that the number of terms to match is not specified at compile time
        Dim sentenceQuery = From sentence In sentences
                            Let w = sentence.Split(New Char() {" ", ",", ".", ";", ":"},
                                                   StringSplitOptions.RemoveEmptyEntries)
                            Where w.Distinct().Intersect(wordsToMatch).Count = wordsToMatch.Count()
                            Select sentence

        ' Execute the query
        For Each str As String In sentenceQuery
            Console.WriteLine(str)
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub

End Class
' Output:
' Historically, the world of data and the world of objects have not been well integrated
```

<span data-ttu-id="5a3e5-107">Die Abfrage funktioniert, indem der Text zuerst in Sätze aufgeteilt wird. Diese Sätze werden wiederum in ein Array von Zeichenfolgen aufgeteilt, das jedes Wort enthält.</span><span class="sxs-lookup"><span data-stu-id="5a3e5-107">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="5a3e5-108">Für jedes dieser Arrays entfernt die <xref:System.Linq.Enumerable.Distinct%2A>-Methode alle Wortduplikate, und anschließend führt die Abfrage einen <xref:System.Linq.Enumerable.Intersect%2A>-Vorgang für das Wortarray und das `wordsToMatch`-Array durch.</span><span class="sxs-lookup"><span data-stu-id="5a3e5-108">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="5a3e5-109">Wenn die Anzahl der Schnittmenge identisch mit der Anzahl des `wordsToMatch`-Arrays ist, werden alle gefundenen Wörter in den Wörtern und der ursprüngliche Satz zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="5a3e5-109">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>

<span data-ttu-id="5a3e5-110">Im Aufruf von <xref:System.String.Split%2A> werden die Satzzeichen als Trennlinien verwendet, damit sie aus der Zeichenfolge entfernt werden können.</span><span class="sxs-lookup"><span data-stu-id="5a3e5-110">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="5a3e5-111">Wenn Sie dies nicht getan haben, haben Sie z.B. eine „ursprüngliche“ Zeichenfolge, die „usprünglich“ nicht mit dem `wordsToMatch`-Array übereinstimmen würde.</span><span class="sxs-lookup"><span data-stu-id="5a3e5-111">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="5a3e5-112">Sie müssen möglicherweise zusätzliche Trennzeichen verwenden, abhängig von den Satzzeichen, die im Quelltext vorkommen.</span><span class="sxs-lookup"><span data-stu-id="5a3e5-112">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="5a3e5-113">Kompilieren des Codes</span><span class="sxs-lookup"><span data-stu-id="5a3e5-113">Compile the code</span></span>

<span data-ttu-id="5a3e5-114">Erstellen Sie ein Visual Basic Konsolen Anwendungsprojekt mit einer- `Imports` Anweisung für den System. Linq-Namespace.</span><span class="sxs-lookup"><span data-stu-id="5a3e5-114">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a3e5-115">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5a3e5-115">See also</span></span>

- [<span data-ttu-id="5a3e5-116">LINQ und Zeichenfolgen (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a3e5-116">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
