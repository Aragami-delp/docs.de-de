---
title: Schnelle Anwendungsentwicklung mit My.Resources und My.Settings
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: ce9a5bf76ba3132f58aa40227a145d8b5bf1591d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349265"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="505c4-102">Schnelle Anwendungsentwicklung mit My.Resources und My.Settings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="505c4-102">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>

<span data-ttu-id="505c4-103">Mit dem Objekt `My.Resources` erhalten Sie Zugriff auf die Anwendungsressourcen und können Ressourcen für Ihre Anwendung dynamisch abrufen.</span><span class="sxs-lookup"><span data-stu-id="505c4-103">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="505c4-104">Abrufen von Ressourcen</span><span class="sxs-lookup"><span data-stu-id="505c4-104">Retrieving Resources</span></span>  

 <span data-ttu-id="505c4-105">Mithilfe des `My.Resources`-Objekts können Sie eine Reihe von Ressourcen abrufen, wie etwa Audiodateien, Symbole, Bilder und Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="505c4-105">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="505c4-106">Sie können beispielsweise auf die kulturspezifischen Ressourcendateien der Anwendung zugreifen.</span><span class="sxs-lookup"><span data-stu-id="505c4-106">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="505c4-107">Im folgenden Beispiel wird das Symbol des Formulars auf das Symbol `Form1Icon` festgelegt, das in der Ressourcendatei der Anwendung gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="505c4-107">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 <span data-ttu-id="505c4-108">Das `My.Resources`-Objekt macht nur globale Ressourcen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="505c4-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="505c4-109">Es bietet keinen Zugriff auf Ressourcendateien, die Formularen zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="505c4-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="505c4-110">Zugriff auf die Formularressourcen erhalten Sie über das Formular.</span><span class="sxs-lookup"><span data-stu-id="505c4-110">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="505c4-111">Ebenso bietet das `My.Settings`-Objekt Zugriff auf die Einstellungen der Anwendung und ermöglicht das dynamische Speichern und Abrufen von Eigenschafteneinstellungen und anderen Informationen für Ihre Anwendung.</span><span class="sxs-lookup"><span data-stu-id="505c4-111">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="505c4-112">Weitere Informationen finden Sie unter [My.Resources-Objekt](../../../visual-basic/language-reference/objects/my-resources-object.md) und [My.Settings-Objekt](../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="505c4-112">For more information, see [My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md) and [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="505c4-113">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="505c4-113">See also</span></span>

- [<span data-ttu-id="505c4-114">My.Resources-Objekt</span><span class="sxs-lookup"><span data-stu-id="505c4-114">My.Resources Object</span></span>](../../../visual-basic/language-reference/objects/my-resources-object.md)
- [<span data-ttu-id="505c4-115">My.Settings-Objekt</span><span class="sxs-lookup"><span data-stu-id="505c4-115">My.Settings Object</span></span>](../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="505c4-116">Zugreifen auf Anwendungseinstellungen</span><span class="sxs-lookup"><span data-stu-id="505c4-116">Accessing Application Settings</span></span>](../../../visual-basic/developing-apps/programming/app-settings/index.md)
