---
title: Ausführen von Aufgaben mit My.Application, My.Computer und My.User
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
ms.openlocfilehash: 55961d6857b690fc2726f541df8a5497a3207928
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411693"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a><span data-ttu-id="14e6a-102">Ausführen von Aufgaben mit My.Application, My.Computer und My.User (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14e6a-102">Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic)</span></span>

<span data-ttu-id="14e6a-103">Die drei zentralen `My`-Objekte, die Zugriff auf Informationen und häufig verwendete Funktionen bieten, sind `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>) und `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span><span class="sxs-lookup"><span data-stu-id="14e6a-103">The three central `My` objects that provide access to information and commonly used functionality are `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), and `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span></span> <span data-ttu-id="14e6a-104">Sie können diese Objekte verwenden, um auf Informationen zuzugreifen, die im Zusammenhang mit der aktuellen Anwendung, dem Computer, auf dem die Anwendung installiert ist, oder dem aktuellen Benutzer der Anwendung stehen.</span><span class="sxs-lookup"><span data-stu-id="14e6a-104">You can use these objects to access information that is related to the current application, the computer that the application is installed on, or the current user of the application, respectively.</span></span>  
  
## <a name="myapplication-mycomputer-and-myuser"></a><span data-ttu-id="14e6a-105">My.Application, My.Computer und My.User</span><span class="sxs-lookup"><span data-stu-id="14e6a-105">My.Application, My.Computer, and My.User</span></span>  

 <span data-ttu-id="14e6a-106">In den folgenden Beispielen wird veranschaulicht, wie Informationen mithilfe von `My` abgerufen werden können.</span><span class="sxs-lookup"><span data-stu-id="14e6a-106">The following examples demonstrate how information can be retrieved using `My`.</span></span>  
  
 [!code-vb[VbVbcnMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbcnMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#2)]  
  
 <span data-ttu-id="14e6a-107">Zusätzlich zum Abrufen von Informationen ermöglichen die Member, die über diese drei Objekte verfügbar gemacht werden, auch das Ausführen von Methoden, die mit diesem Objekt verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="14e6a-107">In addition to retrieving information, the members exposed through these three objects also allow you to execute methods related to that object.</span></span> <span data-ttu-id="14e6a-108">Beispielsweise können Sie auf viele verschiedene Methoden zugreifen, um Dateien zu bearbeiten oder die Registrierung über `My.Computer` zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="14e6a-108">For instance, you can access a variety of methods to manipulate files or update the registry through `My.Computer`.</span></span>  
  
 <span data-ttu-id="14e6a-109">Datei-E/A-Vorgänge gestalten sich mit `My` bedeutend einfacher und schneller, da eine Vielzahl von Methoden und Eigenschaften zum Bearbeiten von Dateien, Verzeichnissen und Laufwerken enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="14e6a-109">File I/O is significantly easier and faster with `My`, which includes a variety of methods and properties for manipulating files, directories, and drives.</span></span> <span data-ttu-id="14e6a-110">Das <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>-Objekt ermöglicht das Lesen aus großen strukturierten Dateien, die Felder mit Trennzeichen oder fester Breite enthalten.</span><span class="sxs-lookup"><span data-stu-id="14e6a-110">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object allows you to read from large structured files that have delimited or fixed-width fields.</span></span> <span data-ttu-id="14e6a-111">In diesem Beispiel wird `TextFieldParser` `reader` geöffnet und zum Lesen aus `C:\TestFolder1\test1.txt` verwendet.</span><span class="sxs-lookup"><span data-stu-id="14e6a-111">This example opens the `TextFieldParser` `reader` and uses it to read from `C:\TestFolder1\test1.txt`.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#23)]  
  
 <span data-ttu-id="14e6a-112">`My.Application` ermöglicht es Ihnen, die Kultur für Ihre Anwendung zu ändern.</span><span class="sxs-lookup"><span data-stu-id="14e6a-112">`My.Application` allows you to change the culture for your application.</span></span> <span data-ttu-id="14e6a-113">Das folgende Beispiel veranschaulicht, wie diese Methode aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="14e6a-113">The following example demonstrates how this method can be called.</span></span>  
  
 [!code-vb[VbVbcnMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="14e6a-114">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="14e6a-114">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [<span data-ttu-id="14e6a-115">Merkmale von "My" auf Grundlage des Projekttyps</span><span class="sxs-lookup"><span data-stu-id="14e6a-115">How My Depends on Project Type</span></span>](how-my-depends-on-project-type.md)
