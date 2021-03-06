---
title: Erweiterte Behandlung von Freihandeingaben
ms.date: 03/30/2017
f1_keywords:
- AutoGeneratedOrientationPage
helpviewer_keywords:
- System.Windows.Input.StylusPlugIns classes
- InkCanvas control [WPF]
- ink [WPF], advanced handling
ms.assetid: abc8481a-f983-416f-b051-9168ac8b2ba3
ms.openlocfilehash: 840ab08faebe760a38ef344fd1c41818a838250b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008940"
---
# <a name="advanced-ink-handling"></a>Erweiterte Behandlung von Freihandeingaben
Die [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] im Lieferumfang der <xref:System.Windows.Controls.InkCanvas>, und ist ein Element, das Sie in Ihrer Anwendung, um sofort zu starten, sammeln und Anzeigen von Freihandeingaben einfügen können. Aber wenn die <xref:System.Windows.Controls.InkCanvas> Steuerelement bietet nicht genug hochgradige Kontrolle, die Sie selbst steuern auf einer höheren Ebene durch Anpassen der eigenen Freihandeingaben und Freihand-Rendering-Klassen mit <xref:System.Windows.Input.StylusPlugIns>.  
  
 Die <xref:System.Windows.Input.StylusPlugIns> Klassen bieten einen Mechanismus zum Implementieren der Steuerung auf niedriger Ebene über <xref:System.Windows.Input.Stylus> Eingabe- und dynamischen Rendern von Freihandeingaben. Die <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> -Klasse bietet einen Mechanismus für die Sie benutzerdefiniertes Verhalten implementieren, und klicken Sie auf die vom Tablettstift für eine optimale Leistung eingehenden Datenstrom anzuwenden. Die <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, ein spezielles <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>, können Sie Sie dynamisch Rendering in Echtzeit Freihanddaten, d. h. die <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Zeichnet Freihandeingaben sofort als <xref:System.Windows.Input.StylusPoint> Daten generiert werden, sodass er angezeigt wird, die vom Tablettstift "flow" das Gerät.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Benutzerdefiniertes Rendern von Freihandeingaben](custom-rendering-ink.md)  
  [Abfangen von Tablettstifteingaben](intercepting-input-from-the-stylus.md)  
  [Erstellen eines Freihandeingabesteuerelements](creating-an-ink-input-control.md)  
  [Das Threadmodell für Freihandeingaben](the-ink-threading-model.md)
