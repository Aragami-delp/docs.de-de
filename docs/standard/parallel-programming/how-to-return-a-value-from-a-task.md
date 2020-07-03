---
title: 'Vorgehensweise: Zurückgeben eines Werts aus einer Aufgabe'
description: Informationen zur Verwendung des Typs „System.Threading.Tasks.Task<TResult>“, um einen Wert aus der Ergebniseigenschaft in .NET zurückzugeben
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
ms.openlocfilehash: 051cef7cac654e4369ec1486884876004370ba0b
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2020
ms.locfileid: "84767974"
---
# <a name="how-to-return-a-value-from-a-task"></a>Vorgehensweise: Zurückgeben eines Werts aus einer Aufgabe
In diesem Beispiel wird gezeigt, wie Sie mit dem <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>-Typ einen Wert aus der <xref:System.Threading.Tasks.Task%601.Result%2A>-Eigenschaft zurückgeben. Für das Beispiel ist es erforderlich, dass das Verzeichnis "C:\Users\Public\Pictures\Sample Pictures\" vorhanden ist und Dateien enthält.  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 Die <xref:System.Threading.Tasks.Task%601.Result%2A>-Eigenschaft sperrt den aufrufenden Thread, bis die Aufgabe abgeschlossen ist.  
  
 Um zu erfahren, wie das Ergebnis eines <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> an eine Fortsetzungsaufgabe übergeben wird, lesen Sie [Verketten von Aufgaben mithilfe von Fortsetzungsaufgaben](chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Siehe auch

- [Aufgabenbasierte asynchrone Programmierung](task-based-asynchronous-programming.md)
- [Lambdaausdrücke in PLINQ und TPL](lambda-expressions-in-plinq-and-tpl.md)
