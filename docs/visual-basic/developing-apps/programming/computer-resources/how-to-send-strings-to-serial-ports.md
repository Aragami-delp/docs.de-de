---
title: 'Gewusst wie: Senden von Zeichenfolgen zu seriellen Anschlüssen'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: f78df9cf1bd75432ea645c4dcc06498915ceee49
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360292"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="bac28-102">Gewusst wie: Senden von Zeichenfolgen zu seriellen Anschlüssen in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bac28-102">How to: Send Strings to Serial Ports in Visual Basic</span></span>

<span data-ttu-id="bac28-103">Dieses Thema beschreibt, wie `My.Computer.Ports` zum Senden von Zeichenfolgen an serielle Ports des Computers in Visual Basic verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="bac28-103">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bac28-104">Beispiel</span><span class="sxs-lookup"><span data-stu-id="bac28-104">Example</span></span>  

 <span data-ttu-id="bac28-105">Dieses Beispiel sendet eine Zeichenfolge an den seriellen COM1-Anschluss.</span><span class="sxs-lookup"><span data-stu-id="bac28-105">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="bac28-106">Möglicherweise müssen Sie auf Ihrem Computer einen anderen seriellen Anschluss verwenden.</span><span class="sxs-lookup"><span data-stu-id="bac28-106">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="bac28-107">Verwenden Sie die `My.Computer.Ports.OpenSerialPort`-Methode, um einen Verweis auf den Anschluss zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="bac28-107">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="bac28-108">Weitere Informationen finden Sie unter <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="bac28-108">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="bac28-109">Der `Using`-Block ermöglicht der Anwendung, den seriellen Anschluss auch dann zu schließen, wenn die eingeschlossene Anweisung eine Ausnahme generiert.</span><span class="sxs-lookup"><span data-stu-id="bac28-109">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="bac28-110">Sämtlicher Code, der den seriellen Anschluss ändert, sollte in diesem Block oder in einem `Try...Catch...Finally`-Block angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bac28-110">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="bac28-111">Die <xref:System.IO.Ports.SerialPort.WriteLine%2A>-Methode sendet die Daten an den seriellen Anschluss.</span><span class="sxs-lookup"><span data-stu-id="bac28-111">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bac28-112">Kompilieren des Codes</span><span class="sxs-lookup"><span data-stu-id="bac28-112">Compiling the Code</span></span>  
  
- <span data-ttu-id="bac28-113">In diesem Beispiel wird davon ausgegangen, dass der Computer `COM1` verwendet.</span><span class="sxs-lookup"><span data-stu-id="bac28-113">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="bac28-114">Stabile Programmierung</span><span class="sxs-lookup"><span data-stu-id="bac28-114">Robust Programming</span></span>  

 <span data-ttu-id="bac28-115">In diesem Beispiel wird davon ausgegangen, dass der Computer `COM1` verwendet; für eine erhöhte Flexibilität sollte der Code es dem Benutzer ermöglichen, den gewünschten seriellen Anschluss aus einer Liste von seriellen Anschlüssen auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="bac28-115">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="bac28-116">Weitere Informationen finden Sie unter [Gewusst wie: Anzeigen von verfügbaren seriellen Anschlüssen](how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="bac28-116">For more information, see [How to: Show Available Serial Ports](how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="bac28-117">Dieses Beispiel verwendet einen `Using`-Block, um sicherzustellen, dass die Anwendung den Anschluss auch dann schließt, wenn eine Ausnahme ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="bac28-117">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="bac28-118">Weitere Informationen finden Sie unter [using-Anweisung](../../../language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="bac28-118">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bac28-119">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="bac28-119">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="bac28-120">Gewusst wie: Wählen mit Modems an seriellen Anschlüssen</span><span class="sxs-lookup"><span data-stu-id="bac28-120">How to: Dial Modems Attached to Serial Ports</span></span>](how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="bac28-121">Gewusst wie: Anzeigen von verfügbaren seriellen Anschlüssen</span><span class="sxs-lookup"><span data-stu-id="bac28-121">How to: Show Available Serial Ports</span></span>](how-to-show-available-serial-ports.md)
