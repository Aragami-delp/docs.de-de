---
title: 'Vorgehensweise: Paralleles Erstellen mehrerer Webanforderungen mit async und await (C#)'
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: 0cfc1d6d1d59dc74fcf5990abb0a9d980a83d7b0
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241798"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a><span data-ttu-id="ce2da-102">Vorgehensweise: Paralleles Erstellen mehrerer Webanforderungen mit async und await (C#)</span><span class="sxs-lookup"><span data-stu-id="ce2da-102">How to make multiple web requests in parallel by using async and await (C#)</span></span>
<span data-ttu-id="ce2da-103">In einer asynchronen Methode werden Aufgaben gestartet, wenn sie erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="ce2da-103">In an async method, tasks are started when they're created.</span></span> <span data-ttu-id="ce2da-104">Der [await](../../../language-reference/operators/await.md)-Operator wird auf die Aufgabe an dem Punkt in der Methode angewendet, an dem die Verarbeitung nicht fortgesetzt werden kann, bis die Aufgabe abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="ce2da-104">The [await](../../../language-reference/operators/await.md) operator is applied to the task at the point in the method where processing can't continue until the task finishes.</span></span> <span data-ttu-id="ce2da-105">Wie das folgende Beispiel zeigt, wird häufig auf eine Aufgabe gewartet, sobald diese erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="ce2da-105">Often a task is awaited as soon as it's created, as the following example shows.</span></span>  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 <span data-ttu-id="ce2da-106">Sie können das Erstellen der Aufgabe jedoch vom Warten auf diese trennen, wenn das Programm weitere Aufgaben ausführen muss, die nicht vom Abschluss dieser Aufgabe abhängig sind.</span><span class="sxs-lookup"><span data-stu-id="ce2da-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn't depend on the completion of the task.</span></span>  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 <span data-ttu-id="ce2da-107">Zwischen dem Starten und dem Erwarten einer Aufgabe können Sie andere Aufgaben starten.</span><span class="sxs-lookup"><span data-stu-id="ce2da-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="ce2da-108">Die weiteren Aufgaben werden implizit parallel ausgeführt, es werden jedoch keine weiteren Threads erstellt.</span><span class="sxs-lookup"><span data-stu-id="ce2da-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="ce2da-109">Das folgende Programm startet drei asynchrone Webdownloads und wartet dann in der Reihenfolge auf sie, in der sie aufgerufen wurden.</span><span class="sxs-lookup"><span data-stu-id="ce2da-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they're called.</span></span> <span data-ttu-id="ce2da-110">Beachten Sie, dass die Aufgaben beim Ausführen des Programms nicht immer in der Reihenfolge abgeschlossen werden, in der sie erstellt wurden und in der auf sie gewartet wird.</span><span class="sxs-lookup"><span data-stu-id="ce2da-110">Notice, when you run the program, that the tasks don't always finish in the order in which they're created and awaited.</span></span> <span data-ttu-id="ce2da-111">Sie beginnen mit der Ausführung zum Zeitpunkt der Erstellung, und eine oder mehrere Aufgaben werden möglicherweise abgeschlossen, bevor die Methode die await-Ausdrücke erreicht.</span><span class="sxs-lookup"><span data-stu-id="ce2da-111">They start to run when they're created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce2da-112">Zum Fertigstellen dieses Projekts muss Visual Studio 2012 oder höher sowie .NET Framework 4.5 oder höher auf dem Computer installiert sein.</span><span class="sxs-lookup"><span data-stu-id="ce2da-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="ce2da-113">Ein weiteres Beispiel, in dem mehrere Aufgaben zur gleichen Zeit gestartet werden, finden Sie unter [Vorgehensweise: Erweitern der asynchronen exemplarischen Vorgehensweise mit Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="ce2da-113">For another example that starts multiple tasks at the same time, see [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>
  
 <span data-ttu-id="ce2da-114">Sie können den Code für dieses Beispiel auf der Seite für [Codebeispiele für Entwickler](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e) herunterladen.</span><span class="sxs-lookup"><span data-stu-id="ce2da-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="ce2da-115">So richten Sie das Projekt ein</span><span class="sxs-lookup"><span data-stu-id="ce2da-115">To set up the project</span></span>  
  
1. <span data-ttu-id="ce2da-116">Führen Sie die folgenden Schritte aus, um eine WPF-Anwendung einzurichten.</span><span class="sxs-lookup"><span data-stu-id="ce2da-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="ce2da-117">Ausführliche Anweisungen für diese Schritte finden Sie unter [Exemplarische Vorgehensweise: Zugreifen auf das Web mit „async“ und „await“ (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="ce2da-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="ce2da-118">Erstellen Sie eine WPF-Anwendung, die ein Textfeld und eine Schaltfläche enthält.</span><span class="sxs-lookup"><span data-stu-id="ce2da-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="ce2da-119">Benennen Sie die Schaltfläche mit `startButton` und das Textfeld mit `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="ce2da-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    - <span data-ttu-id="ce2da-120">Fügen Sie einen Verweis für <xref:System.Net.Http> hinzu.</span><span class="sxs-lookup"><span data-stu-id="ce2da-120">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    - <span data-ttu-id="ce2da-121">Fügen Sie in der Datei „MainWindow.xaml.cs“ ein `using`-Verzeichnis für `System.Net.Http` ein.</span><span class="sxs-lookup"><span data-stu-id="ce2da-121">In the MainWindow.xaml.cs file, add a `using` directive for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="ce2da-122">So fügen Sie den Code hinzu</span><span class="sxs-lookup"><span data-stu-id="ce2da-122">To add the code</span></span>  
  
1. <span data-ttu-id="ce2da-123">Doppelklicken Sie im Entwurfsfenster „MainWindow.xaml“ auf die Schaltfläche, um den `startButton_Click`-Ereignishandler in „MainWindow.xaml.cs“ zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ce2da-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2. <span data-ttu-id="ce2da-124">Kopieren Sie den folgenden Code, und fügen Sie ihn in den Text von `startButton_Click` in „MainWindow.xaml.cs“ ein.</span><span class="sxs-lookup"><span data-stu-id="ce2da-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     <span data-ttu-id="ce2da-125">Der Code ruft die asynchrone Methode `CreateMultipleTasksAsync` auf, die die Anwendung steuert.</span><span class="sxs-lookup"><span data-stu-id="ce2da-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3. <span data-ttu-id="ce2da-126">Fügen Sie dem Projekt die folgenden Unterstützungsmethoden hinzu:</span><span class="sxs-lookup"><span data-stu-id="ce2da-126">Add the following support methods to the project:</span></span>  
  
    - <span data-ttu-id="ce2da-127">`ProcessURLAsync` verwendet eine <xref:System.Net.Http.HttpClient>-Methode, um die Inhalte einer Website als Bytearray herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="ce2da-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="ce2da-128">Die Unterstützungsmethode `ProcessURLAsync` wird daraufhin angezeigt und gibt die Länge des Arrays zurück.</span><span class="sxs-lookup"><span data-stu-id="ce2da-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    - <span data-ttu-id="ce2da-129">`DisplayResults` zeigt die Anzahl von Bytes im Bytearray für jede URL an.</span><span class="sxs-lookup"><span data-stu-id="ce2da-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="ce2da-130">Diese Anzeige wird aufgerufen, wenn alle Aufgaben den Download abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="ce2da-130">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="ce2da-131">Kopieren Sie die folgenden Methoden, und fügen Sie sie nach dem `startButton_Click`-Ereignishandler in „MainWindow.xaml.cs“ ein.</span><span class="sxs-lookup"><span data-stu-id="ce2da-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    async Task<int> ProcessURLAsync(string url, HttpClient client)  
    {  
        var byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
  
    private void DisplayResults(string url, byte[] content)  
    {  
        // Display the length of each website. The string format
        // is designed to be used with a monospaced font, such as  
        // Lucida Console or Global Monospace.  
        var bytes = content.Length;  
        // Strip off the "https://".  
        var displayURL = url.Replace("https://", "");  
        resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
    }  
    ```  
  
4. <span data-ttu-id="ce2da-132">Definieren Sie schließlich die `CreateMultipleTasksAsync`-Methode, die die folgenden Schritte ausführt.</span><span class="sxs-lookup"><span data-stu-id="ce2da-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    - <span data-ttu-id="ce2da-133">Die Methode deklariert ein `HttpClient`-Objekt, das Sie für den Zugriff auf die <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>-Methode in `ProcessURLAsync` benötigen.</span><span class="sxs-lookup"><span data-stu-id="ce2da-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    - <span data-ttu-id="ce2da-134">Die Methode erstellt und startet drei Aufgaben vom Typ <xref:System.Threading.Tasks.Task%601>, wobei `TResult` eine ganze Zahl ist.</span><span class="sxs-lookup"><span data-stu-id="ce2da-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="ce2da-135">Beim Abschließen jeder Aufgabe zeigt `DisplayResults` die URL der Aufgabe sowie die Länge der heruntergeladenen Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="ce2da-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="ce2da-136">Da die Aufgaben asynchron ausgeführt werden, kann sich die Reihenfolge, in der die Ergebnisse angezeigt werden, von der Reihenfolge, in der sie deklariert wurden, unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="ce2da-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    - <span data-ttu-id="ce2da-137">Die Methode erwartet den Abschluss jeder Aufgabe.</span><span class="sxs-lookup"><span data-stu-id="ce2da-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="ce2da-138">Jeder `await`-Operator hält die Ausführung von `CreateMultipleTasksAsync` an, bis die erwartete Aufgabe abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="ce2da-138">Each `await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="ce2da-139">Der Operator ruft außerdem den Rückgabewert des Aufrufs von `ProcessURLAsync` von jeder abgeschlossenen Aufgabe ab.</span><span class="sxs-lookup"><span data-stu-id="ce2da-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    - <span data-ttu-id="ce2da-140">Wenn die Aufgaben abgeschlossen und die ganzzahligen Werte abgerufen wurden, werden die Längen der Websites von der Methode summiert, und das Ergebnis wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ce2da-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="ce2da-141">Kopieren Sie die folgende Methode, und fügen Sie sie in Ihre Projektmappe ein.</span><span class="sxs-lookup"><span data-stu-id="ce2da-141">Copy the following method, and paste it into your solution.</span></span>  
  
    ```csharp  
    private async Task CreateMultipleTasksAsync()  
    {  
        // Declare an HttpClient object, and increase the buffer size. The  
        // default buffer size is 65,536.  
        HttpClient client =  
            new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
        // Create and start the tasks. As each task finishes, DisplayResults
        // displays its length.  
        Task<int> download1 =
            ProcessURLAsync("https://msdn.microsoft.com", client);  
        Task<int> download2 =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
        Task<int> download3 =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
        // Await each task.  
        int length1 = await download1;  
        int length2 = await download2;  
        int length3 = await download3;  
  
        int total = length1 + length2 + length3;  
  
        // Display the total count for the downloaded websites.  
        resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
    }  
    ```  
  
5. <span data-ttu-id="ce2da-142">Drücken Sie die Taste F5, um das Programm auszuführen, und klicken Sie dann auf die Schaltfläche **Starten** .</span><span class="sxs-lookup"><span data-stu-id="ce2da-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="ce2da-143">Führen Sie das Programm mehrmals aus, um sicherzustellen, dass die drei Aufgaben nicht immer in derselben Reihenfolge abgeschlossen werden und dass die Reihenfolge, in der sie abgeschlossen werden, nicht notwendigerweise der Reihenfolge entspricht, in der sie erstellt wurden und in der auf sie gewartet wird.</span><span class="sxs-lookup"><span data-stu-id="ce2da-143">Run the program several times to verify that the three tasks don't always finish in the same order and that the order in which they finish isn't necessarily the order in which they're created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce2da-144">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ce2da-144">Example</span></span>  
 <span data-ttu-id="ce2da-145">Der folgende Code umfasst das vollständige Beispiel.</span><span class="sxs-lookup"><span data-stu-id="ce2da-145">The following code contains the full example.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
  
// Add the following using directive, and add a reference for System.Net.Http.  
using System.Net.Http;  
  
namespace AsyncExample_MultipleTasks  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
            await CreateMultipleTasksAsync();  
            resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task CreateMultipleTasksAsync()  
        {  
            // Declare an HttpClient object, and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client =  
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Create and start the tasks. As each task finishes, DisplayResults
            // displays its length.  
            Task<int> download1 =
                ProcessURLAsync("https://msdn.microsoft.com", client);  
            Task<int> download2 =
                ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
            Task<int> download3 =
                ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
            // Await each task.  
            int length1 = await download1;  
            int length2 = await download2;  
            int length3 = await download3;  
  
            int total = length1 + length2 + length3;  
  
            // Display the total count for the downloaded websites.  
            resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }  
  
        async Task<int> ProcessURLAsync(string url, HttpClient client)  
        {  
            var byteArray = await client.GetByteArrayAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "https://".  
            var displayURL = url.Replace("https://", "");  
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce2da-146">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ce2da-146">See also</span></span>

- [<span data-ttu-id="ce2da-147">Exemplarische Vorgehensweise: Zugreifen auf das Web mit async und await (C#)</span><span class="sxs-lookup"><span data-stu-id="ce2da-147">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="ce2da-148">Asynchrone Programmierung mit „async“ und „await“ (C#)</span><span class="sxs-lookup"><span data-stu-id="ce2da-148">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="ce2da-149">Vorgehensweise: Erweitern der asynchronen exemplarischen Vorgehensweise mit Task.WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="ce2da-149">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
