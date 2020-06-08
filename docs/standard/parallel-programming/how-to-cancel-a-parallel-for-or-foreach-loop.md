---
title: 'Gewusst wie: Abbrechen einer Parallel.For-Schleife oder einer ForEach-Schleife'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
ms.openlocfilehash: d29137127dd47844f8f08d3ac689cf2827d9efe2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288224"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="1c1ff-102">Gewusst wie: Abbrechen einer Parallel.For-Schleife oder einer ForEach-Schleife</span><span class="sxs-lookup"><span data-stu-id="1c1ff-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="1c1ff-103">Die <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>- und <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>-Methode unterstützen den Abbruch durch die Verwendung von Abbruchtoken.</span><span class="sxs-lookup"><span data-stu-id="1c1ff-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="1c1ff-104">Weitere Informationen über Abbrüche im Allgemeinen finden Sie unter [Abbruch in verwalteten Threads](../threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="1c1ff-104">For more information about cancellation in general, see [Cancellation](../threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="1c1ff-105">Übergeben Sie in einer parallelen Schleife das <xref:System.Threading.CancellationToken> mit dem <xref:System.Threading.Tasks.ParallelOptions>-Parameter an die Methode, und schließen Sie den parallelen Aufruf in einen Try-Catch-Block ein.</span><span class="sxs-lookup"><span data-stu-id="1c1ff-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c1ff-106">Beispiel</span><span class="sxs-lookup"><span data-stu-id="1c1ff-106">Example</span></span>  
 <span data-ttu-id="1c1ff-107">Im folgenden Beispiel wird der Abbruch des Aufrufs einer <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>-Methode veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="1c1ff-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1c1ff-108">Sie können den gleichen Ansatz auf einen <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>-Aufruf anwenden.</span><span class="sxs-lookup"><span data-stu-id="1c1ff-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="1c1ff-109">Wenn das Token, das den Abbruch signalisiert, mit dem in der <xref:System.Threading.Tasks.ParallelOptions>-Instanz angegebenen identisch ist, löst die parallele Schleife beim Abbruch eine einzelne <xref:System.OperationCanceledException> aus.</span><span class="sxs-lookup"><span data-stu-id="1c1ff-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="1c1ff-110">Wenn ein anderes Token den Abbruch verursacht, löst die Schleife eine <xref:System.AggregateException> mit einer <xref:System.OperationCanceledException> als InnerException aus.</span><span class="sxs-lookup"><span data-stu-id="1c1ff-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c1ff-111">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1c1ff-111">See also</span></span>

- [<span data-ttu-id="1c1ff-112">Datenparallelität</span><span class="sxs-lookup"><span data-stu-id="1c1ff-112">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="1c1ff-113">Lambdaausdrücke in PLINQ und TPL</span><span class="sxs-lookup"><span data-stu-id="1c1ff-113">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
