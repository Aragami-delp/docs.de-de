---
title: 'Vorgehensweise: Paralleles Erstellen mehrerer Webanforderungen mit Async und Await'
ms.date: 07/20/2015
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
ms.openlocfilehash: 40bab392af94ba941c2562e885a8d2e08aeea5b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396583"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a>How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic) (Gewusst wie: Paralleles Erstellen mehrerer Webanforderungen mit Async und Await (Visual Basic))

In einer asynchronen Methode werden Aufgaben gestartet, wenn sie erstellt werden. Der [Erwartungs Operator wird](../../../language-reference/operators/await-operator.md) auf die Aufgabe an dem Punkt in der Methode angewendet, an dem die Verarbeitung nicht fortgesetzt werden kann, bis die Aufgabe abgeschlossen ist. Häufig wird eine Aufgabe erwartet, sobald sie erstellt wird, wie das folgende Beispiel zeigt.

```vb
Dim result = Await someWebAccessMethodAsync(url)
```

Sie können das Erstellen der Aufgabe vom Erwarten der Aufgabe jedoch trennen, wenn das Programm weitere Arbeit durchführen muss, die nicht vom Abschluss der Aufgabe abhängig ist.

```vb
' The following line creates and starts the task.
Dim myTask = someWebAccessMethodAsync(url)

' While the task is running, you can do other work that does not depend
' on the results of the task.
' . . . . .

' The application of Await suspends the rest of this method until the task is
' complete.
Dim result = Await myTask
```

Zwischen dem Starten und dem Erwarten einer Aufgabe können Sie andere Aufgaben starten. Die weiteren Aufgaben werden implizit parallel ausgeführt, es werden jedoch keine weiteren Threads erstellt.

Das folgende Programm startet drei asynchrone Webdownloads und erwartet diese dann in der Reihenfolge, in der sie aufgerufen wurden. Beachten Sie, dass die Aufgaben beim Ausführen des Programms nicht immer in der Reihenfolge abgeschlossen werden, in der sie erstellt und erwartet werden. Sie beginnen mit der Ausführung, wenn sie erstellt werden, und eine oder mehrere Aufgaben werden u. U. abgeschlossen, bevor die Methode die await-Ausdrucke erreicht.

> [!NOTE]
> Zum Fertigstellen dieses Projekts muss Visual Studio 2012 oder höher sowie .NET Framework 4.5 oder höher auf dem Computer installiert sein.

Ein weiteres Beispiel, in dem mehrere Aufgaben gleichzeitig gestartet werden, finden Sie unter Gewusst wie: Erweitern der asynchronen exemplarischen Vorgehensweise [mithilfe von "Task. alle" (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).

Sie können den Code für dieses Beispiel auf der Seite für [Codebeispiele für Entwickler](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e) herunterladen.

### <a name="to-set-up-the-project"></a>So richten Sie das Projekt ein

1. Führen Sie die folgenden Schritte aus, um eine WPF-Anwendung einzurichten. Ausführliche Anweisungen zu diesen Schritten finden Sie unter Exemplarische Vorgehensweise [: Zugreifen auf das Web mit Async und warten (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).

    - Erstellen Sie eine WPF-Anwendung, die ein Textfeld und eine Schaltfläche enthält. Benennen Sie die Schaltfläche mit `startButton` und das Textfeld mit `resultsTextBox`.

    - Fügen Sie einen Verweis für <xref:System.Net.Http> hinzu.

    - Fügen Sie in der Datei "MainWindow. XAML. vb" eine- `Imports` Anweisung für hinzu `System.Net.Http` .

### <a name="to-add-the-code"></a>So fügen Sie den Code hinzu

1. Doppelklicken Sie im Entwurfs Fenster MainWindow. XAML auf die Schaltfläche, um den `startButton_Click` Ereignishandler in "MainWindow. XAML. vb" zu erstellen.

2. Kopieren Sie den folgenden Code, und fügen Sie ihn in " `startButton_Click` MainWindow. XAML. vb" in den Text von ein.

    ```vb
    resultsTextBox.Clear()
    Await CreateMultipleTasksAsync()
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    ```

     Der Code ruft die asynchrone Methode `CreateMultipleTasksAsync` auf, die die Anwendung steuert.

3. Fügen Sie dem Projekt die folgenden Unterstützungsmethoden hinzu:

    - `ProcessURLAsync` verwendet eine <xref:System.Net.Http.HttpClient>-Methode, um die Inhalte einer Website als Bytearray herunterzuladen. Die Unterstützungsmethode `ProcessURLAsync` wird daraufhin angezeigt und gibt die Länge des Arrays zurück.

    - `DisplayResults` zeigt die Anzahl von Bytes im Bytearray für jede URL an. Diese Anzeige wird aufgerufen, wenn alle Aufgaben den Download abgeschlossen haben.

     Kopieren Sie die folgenden Methoden, und fügen Sie Sie nach dem- `startButton_Click` Ereignishandler in MainWindow. XAML. vb ein.

    ```vb
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
    ```

4. Definieren Sie schließlich die `CreateMultipleTasksAsync`-Methode, die die folgenden Schritte ausführt.

    - Die Methode deklariert ein `HttpClient`-Objekt, das Sie für den Zugriff auf die <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>-Methode in `ProcessURLAsync` benötigen.

    - Die Methode erstellt und startet drei Aufgaben vom Typ <xref:System.Threading.Tasks.Task%601>, wobei `TResult` eine ganze Zahl ist. Beim Abschließen jeder Aufgabe zeigt `DisplayResults` die URL der Aufgabe sowie die Länge der heruntergeladenen Inhalte an. Da die Aufgaben asynchron ausgeführt werden, kann sich die Reihenfolge, in der die Ergebnisse angezeigt werden, von der Reihenfolge, in der sie deklariert wurden, unterscheiden.

    - Die Methode erwartet den Abschluss jeder Aufgabe. Jeder `Await`-Operator hält die Ausführung von `CreateMultipleTasksAsync` an, bis die erwartete Aufgabe abgeschlossen ist. Der Operator ruft außerdem den Rückgabewert des Aufrufs von `ProcessURLAsync` von jeder abgeschlossenen Aufgabe ab.

    - Wenn die Aufgaben abgeschlossen und die ganzzahligen Werte abgerufen wurden, werden die Längen der Websites von der Methode summiert, und das Ergebnis wird angezeigt.

     Kopieren Sie die folgende Methode, und fügen Sie sie in Ihre Projektmappe ein.

    ```vb
    Private Async Function CreateMultipleTasksAsync() As Task

        ' Declare an HttpClient object, and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Create and start the tasks. As each task finishes, DisplayResults
        ' displays its length.
        Dim download1 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com", client)
        Dim download2 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)
        Dim download3 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)

        ' Await each task.
        Dim length1 As Integer = Await download1
        Dim length2 As Integer = Await download2
        Dim length3 As Integer = Await download3

        Dim total As Integer = length1 + length2 + length3

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function
    ```

5. Drücken Sie die Taste F5, um das Programm auszuführen, und klicken Sie dann auf die Schaltfläche **Starten** .

     Führen Sie das Programm mehrmals aus, um sicherzustellen, dass die drei Aufgaben nicht immer in derselben Reihenfolge abgeschlossen werden und dass die Reihenfolge, in der sie abgeschlossen werden, nicht notwendigerweise der Reihenfolge entspricht, in der sie erstellt und erwartet werden.

## <a name="example"></a>Beispiel

Der folgende Code umfasst das vollständige Beispiel.

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
        resultsTextBox.Clear()
        Await CreateMultipleTasksAsync()
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    End Sub

    Private Async Function CreateMultipleTasksAsync() As Task

        ' Declare an HttpClient object, and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Create and start the tasks. As each task finishes, DisplayResults
        ' displays its length.
        Dim download1 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com", client)
        Dim download2 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)
        Dim download3 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)

        ' Await each task.
        Dim length1 As Integer = Await download1
        Dim length2 As Integer = Await download2
        Dim length3 As Integer = Await download3

        Dim total As Integer = length1 + length2 + length3

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
End Class
```

## <a name="see-also"></a>Weitere Informationen

- [Exemplarische Vorgehensweise: Zugreifen auf das Web mit Async und Await ( Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Asynchronous Programming with Async and Await (Visual Basic) (Asynchrone Programmierung mit Async und Await (Visual Basic))](index.md)
- [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md) (Gewusst wie: Erweitern der asynchronen exemplarischen Vorgehensweise mit Task.WhenAll (Visual Basic))
