---
title: Verarbeiten von XML-Daten im Arbeitsspeicher
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
ms.openlocfilehash: 06863d162a9f9fbf67f41cb12ea4fbb1935b424d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291278"
---
# <a name="processing-xml-data-in-memory"></a>Verarbeiten von XML-Daten im Arbeitsspeicher
Das Microsoft .NET Framework enthält drei Modelle für die Verarbeitung von XML-Daten: die <xref:System.Xml.XmlDocument>-Klasse, die <xref:System.Xml.XPath.XPathDocument>-Klasse sowie [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) und [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
 Die <xref:System.Xml.XmlDocument>-Klasse implementiert die W3C-Empfehlungen "Document Object Model Level 1" und "Document Object Model (DOM) Level 2 Core Specification". DOM ist eine Strukturdarstellung eines XML-Dokuments im Arbeitsspeicher (Cache). Mit dem <xref:System.Xml.XmlDocument> und seinen verwandten Klassen können Sie XML-Dokumente erstellen, Daten laden und auf diese zugreifen, Daten ändern und Änderungen speichern.  
  
 Die <xref:System.Xml.XPath.XPathDocument>-Klasse ist ein schreibgeschützter Datenspeicher im Arbeitsspeicher, der auf dem XPath-Datenmodell basiert. Die <xref:System.Xml.XPath.XPathNavigator>-Klasse bietet Optionen zur Bearbeitung und zum Navigieren mit einem Cursormodell in XML-Dokumenten, die in der schreibgeschützten <xref:System.Xml.XPath.XPathDocument>-Klasse oder in der <xref:System.Xml.XmlDocument>-Klasse enthalten sind.  
  
 [LINQ to XML](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) ist ein mit .NET Framework 3.5 eingeführtes Modell zum Verarbeiten von XML-Daten. Hierbei handelt es sich um ein im Arbeitsspeicher gespeichertes Modell, das auf [Language Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md) basiert. LINQ erweitert die Sprachsyntax von C# und Visual Basic um neue Abfragefunktionen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Verarbeiten von XML-Daten mithilfe des DOM](process-xml-data-using-the-dom-model.md)  
 Erläutert die Verwendung des <xref:System.Xml.XmlDocument> und seiner verwandten Klassen zur Verarbeitung von XML-Daten.  
  
 [Verarbeiten von XML-Daten mithilfe des XPath-Datenmodells](process-xml-data-using-the-xpath-data-model.md)  
 Erläutert die Verwendung der Klassen <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument> und <xref:System.Xml.XPath.XPathNavigator> zur Verarbeitung von XML-Daten.  
  
 [Verarbeitung von XML-Daten mit LINQ to XML](process-xml-data-using-linq-to-xml.md)  
 Enthält eine kurze Übersicht über LINQ to XML sowie Links zur LINQ to XML-Dokumentation.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [XML-Dokumente und -Daten](index.md)
