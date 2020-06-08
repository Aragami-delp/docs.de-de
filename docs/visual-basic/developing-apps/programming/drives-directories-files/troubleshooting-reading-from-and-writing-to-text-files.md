---
title: 'Problembehandlung: Lesen aus und Schreiben in Textdateien'
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
ms.openlocfilehash: 8af4160d09f39f2622a007aef793173d614a8b44
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406624"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a>Problembehandlung: Lesen aus und Schreiben in Textdateien (Visual Basic)

Dieses Thema behandelt häufige Probleme beim Arbeiten mit Textdateien und bietet entsprechende Lösungsansätze an.  
  
## <a name="common-problems"></a>Häufige Probleme  

 Zu den häufigsten Probleme beim Arbeiten mit Textdateien zählen u.a. Sicherheitsausnahmen, Dateicodierungen oder ungültige Pfade.  
  
### <a name="security-exceptions"></a>Sicherheitsausnahmen  

 Eine <xref:System.Security.SecurityException> wird ausgelöst, wenn ein Sicherheitsfehler auftritt. Dies geschieht häufig, wenn dem Benutzer notwendige Berechtigungen fehlen; es kann möglicherweise durch das Hinzufügen von Berechtigungen oder die Arbeit mit Dateien in einem isolierten Speicher behoben werden.  
  
### <a name="file-encodings"></a>Dateicodierungen  

 Dateicodierungen, auch als Zeichencodierungen bezeichnet, geben an, wie Zeichen bei der Textverarbeitung dargestellt werden. Unerwartete Zeichen in einer Textdatei können aufgrund einer falschen Codierung auftreten. Für die meisten Dateien ist eine Codierung vielleicht einer anderen vorzuziehen, je nachdem, welche Sprachzeichen sie verarbeiten oder nicht verarbeiten kann. Unicode wird jedoch in der Regel empfohlen. Weitere Informationen finden Sie unter [Dateicodierungen](file-encodings.md) und <xref:System.Text.Encoding>.  
  
### <a name="incorrect-paths"></a>Falsche Pfade  

 Beim Analysieren von Dateipfaden, insbesondere bei relativen Pfaden, ist es einfach, die falschen Daten bereitzustellen. Viele Probleme können korrigiert werden, indem Sie sicherstellen, dass Sie den richtigen Pfad angeben. Weitere Informationen finden Sie unter [Vorgehensweise: Analysieren von Dateipfaden](how-to-parse-file-paths.md).  
  
## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [Lesen aus Dateien](reading-from-files.md)
- [Schreiben in Dateien](writing-to-files.md)
- [Analysieren von Textdateien mit dem TextFieldParser-Objekt](parsing-text-files-with-the-textfieldparser-object.md)
