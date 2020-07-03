---
title: Schnelle Anwendungsentwicklung mit My.Resources und My.Settings
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: fd1ec25582e919b84235502f5921edfbc6e1dade
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990209"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>Schnelle Anwendungsentwicklung mit My.Resources und My.Settings (Visual Basic)

Mit dem Objekt `My.Resources` erhalten Sie Zugriff auf die Anwendungsressourcen und können Ressourcen für Ihre Anwendung dynamisch abrufen.  
  
## <a name="retrieving-resources"></a>Abrufen von Ressourcen  

 Mithilfe des `My.Resources`-Objekts können Sie eine Reihe von Ressourcen abrufen, wie etwa Audiodateien, Symbole, Bilder und Zeichenfolgen. Sie können beispielsweise auf die kulturspezifischen Ressourcendateien der Anwendung zugreifen. Im folgenden Beispiel wird das Symbol des Formulars auf das Symbol `Form1Icon` festgelegt, das in der Ressourcendatei der Anwendung gespeichert ist.  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 Das `My.Resources`-Objekt macht nur globale Ressourcen verfügbar. Es bietet keinen Zugriff auf Ressourcendateien, die Formularen zugeordnet sind. Zugriff auf die Formularressourcen erhalten Sie über das Formular.  
  
 Ebenso bietet das `My.Settings`-Objekt Zugriff auf die Einstellungen der Anwendung und ermöglicht das dynamische Speichern und Abrufen von Eigenschafteneinstellungen und anderen Informationen für Ihre Anwendung. Weitere Informationen finden Sie unter [My.Resources-Objekt](../../language-reference/objects/my-resources-object.md) und [My.Settings-Objekt](../../language-reference/objects/my-settings-object.md).  
  
## <a name="see-also"></a>Siehe auch

- [My.Resources-Objekt](../../language-reference/objects/my-resources-object.md)
- [My.Settings-Objekt](../../language-reference/objects/my-settings-object.md)
- [Zugreifen auf Anwendungseinstellungen](../programming/app-settings/index.md)
