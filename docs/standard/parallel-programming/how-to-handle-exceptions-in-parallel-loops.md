---
title: 'Gewusst wie: Behandeln von Ausnahmen in parallelen Schleifen'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
ms.openlocfilehash: 87405425e85ed16d10b3e8b382c6e414fff10ddf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278531"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a>Gewusst wie: Behandeln von Ausnahmen in parallelen Schleifen
Die <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>- und <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>-Überladungen verfügen über keinen speziellen Mechanismus zur Behandlung von Ausnahmen, die möglicherweise ausgelöst werden. In dieser Hinsicht ähneln sie herkömmlichen `for`- und `foreach`-Schleifen (`For` und `For Each` in Visual Basic). Eine nicht behandelte Ausnahme bewirkt, dass die Schleife sofort beendet wird, sobald alle momentan laufenden Iterationen abgeschlossen sind.
  
 Wenn Sie Parallelschleifen eigene Logik zur Ausnahmebehandlung hinzufügen, behandeln Sie den Fall, in dem ähnliche Ausnahmen in mehreren Threads gleichzeitig ausgelöst werden können, sowie den Fall, in dem eine in einem Thread ausgelöste Ausnahme bewirkt, dass eine andere Ausnahme in einem anderen Thread ausgelöst wird. Sie können beide Fälle behandeln, indem Sie alle Ausnahmen der Schleife in einer <xref:System.AggregateException?displayProperty=nameWithType> umschließen. Im folgenden Beispiel wird ein möglicher Ansatz gezeigt.  
  
> [!NOTE]
> Wenn "Nur eigenen Code" aktiviert ist, unterbricht Visual Studio die Ausführung in einigen Fällen in der Zeile, die die Ausnahme auslöst, und eine Fehlermeldung zu einer nicht vom Benutzercode behandelten Ausnahme wird angezeigt. Dieser Fehler hat keine Auswirkungen. Sie können F5 drücken, um den Vorgang fortzusetzen. In diesem Fall wird das im nachstehenden Beispiel veranschaulichte Ausnahmebehandlungsverhalten angewendet. Um zu verhindern, dass Visual Studio die Ausführung beim ersten Fehler unterbricht, deaktivieren Sie unter **Extras, Optionen, Debugging, Allgemein** das Kontrollkästchen „Nur eigenen Code“.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel werden alle Ausnahmen abgefangen und dann in einer <xref:System.AggregateException?displayProperty=nameWithType> umschlossen, die ausgelöst wird. Der Aufrufer kann entscheiden, welche Ausnahmen behandelt werden.  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a>Weitere Informationen

- [Datenparallelität](data-parallelism-task-parallel-library.md)
- [Lambdaausdrücke in PLINQ und TPL](lambda-expressions-in-plinq-and-tpl.md)
