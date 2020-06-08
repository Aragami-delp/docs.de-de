---
title: 'Vorgehensweise: Lesen von Anwendungseinstellungen'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 9b326341c54d652479776e3ab93a2b140f4531e0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410139"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="f5e24-102">Vorgehensweise: Lesen von Anwendungseinstellungen in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f5e24-102">How to: Read Application Settings in Visual Basic</span></span>

<span data-ttu-id="f5e24-103">Sie können eine Benutzereinstellung lesen, indem Sie auf die Einstellung der Eigenschaft im `My.Settings`-Objekt zugreifen.</span><span class="sxs-lookup"><span data-stu-id="f5e24-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="f5e24-104">Das `My.Settings`-Objekt macht jede Einstellung als Eigenschaft verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f5e24-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="f5e24-105">Der Eigenschaftsname ist identisch mit dem Einstellungsnamen, und der Eigenschaftentyp entspricht dem Typ der Einstellung.</span><span class="sxs-lookup"><span data-stu-id="f5e24-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="f5e24-106">Der **Bereich** der Einstellung gibt an, ob die Eigenschaft schreibgeschützt ist; die Eigenschaft für den Bereich **Anwendung** ist schreibgeschützt, während die Eigenschaft für die Bereichseinstellung **Benutzer** über einen Lese-/Schreibzugriff verfügt.</span><span class="sxs-lookup"><span data-stu-id="f5e24-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="f5e24-107">Weitere Informationen finden Sie unter [My.Settings-Objekt](../../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="f5e24-107">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5e24-108">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f5e24-108">Example</span></span>  

 <span data-ttu-id="f5e24-109">In diesem Beispiel wird der Wert der `Nickname`-Einstellung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f5e24-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="f5e24-110">Damit dieses Beispiel funktioniert, muss Ihre Anwendung eine `Nickname`-Einstellung vom Typ `String` aufweisen.</span><span class="sxs-lookup"><span data-stu-id="f5e24-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="f5e24-111">Weitere Informationen finden Sie unter [Verwalten von Anwendungseinstellungen (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="f5e24-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5e24-112">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f5e24-112">See also</span></span>

- [<span data-ttu-id="f5e24-113">My.Settings-Objekt</span><span class="sxs-lookup"><span data-stu-id="f5e24-113">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="f5e24-114">How to: Ändern von Benutzereinstellungen in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f5e24-114">How to: Change User Settings in Visual Basic</span></span>](how-to-change-user-settings.md)
- [<span data-ttu-id="f5e24-115">How to: Beibehalten von Benutzereinstellungen in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f5e24-115">How to: Persist User Settings in Visual Basic</span></span>](how-to-persist-user-settings.md)
- [<span data-ttu-id="f5e24-116">How to: Erstellen von Eigenschaftenrastern für Benutzereinstellungen in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f5e24-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="f5e24-117">Verwalten von Anwendungseinstellungen (.NET)</span><span class="sxs-lookup"><span data-stu-id="f5e24-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
