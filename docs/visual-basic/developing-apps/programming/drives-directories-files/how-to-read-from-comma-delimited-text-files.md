---
title: 'Vorgehensweise: Lesen aus durch Kommas getrennten Textdateien'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: ba62a0226a1a83326cbc7ab393d135763a7c7cb2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411641"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a>Gewusst wie: Lesen aus durch Kommas getrennten Textdateien in Visual Basic

Das `TextFieldParser`-Objekt bietet eine Möglichkeit, strukturierte Textdateien wie Protokolle einfach und effizient zu analysieren. Die `TextFieldType`-Eigenschaft definiert, ob es sich um eine Datei mit Trennzeichen oder mit Textfeldern fester Breite handelt.  
  
### <a name="to-parse-a-comma-delimited-text-file"></a>Analysieren einer durch Trennzeichen getrennten Textdatei  
  
1. Erstellen Sie einen neuen `TextFieldParser`. Der folgende Code erstellt den `TextFieldParser` namens `MyReader` und öffnet die Datei `test.txt`.  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. Definieren Sie den `TextField`-Typ und das Trennzeichen. Der folgende Code definiert die `TextFieldType`-Eigenschaft als `Delimited` und das Trennzeichen als „,“.  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. Durchlaufen Sie die Felder in der Datei. Wenn Zeilen fehlerhaft sind, einen Fehler melden und die Analyse fortsetzen. Der folgende Code durchläuft die Datei, zeigt der Reihe nach jedes Feld an und meldet alle Felder, die nicht korrekt formatiert sind.  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. Schließen Sie die Blöcke `While` und `Using` mit `End While` und `End Using`.  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a>Beispiel  

 In diesem Beispiel wird aus der Datei `test.txt` gelesen.  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a>Stabile Programmierung  

 Die folgenden Bedingungen können einen Ausnahmefehler verursachen:  
  
- Eine Zeile kann nicht mit dem angegebenen Format analysiert werden (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Die Ausnahmemeldung gibt die Zeile an, die die Ausnahme verursacht, während der in der Zeile enthaltene Text der <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A>-Eigenschaft zugewiesen wird.  
  
- Die angegebene Datei ist nicht vorhanden (<xref:System.IO.FileNotFoundException>).  
  
- Eine teilweise vertrauenswürdige Situation, in der der Benutzer nicht über ausreichende Berechtigungen für den Dateizugriff verfügt. (<xref:System.Security.SecurityException>).  
  
- Der Pfad ist zu lang (<xref:System.IO.PathTooLongException>).  
  
- Der Benutzer hat keine ausreichende Berechtigungen für den Dateizugriff (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [Gewusst wie: Lesen aus einer Textdatei mit fester Breite](how-to-read-from-fixed-width-text-files.md)
- [Gewusst wie: Lesen aus Textdateien mit mehreren Formaten](how-to-read-from-text-files-with-multiple-formats.md)
- [Analysieren von Textdateien mit dem TextFieldParser-Objekt](parsing-text-files-with-the-textfieldparser-object.md)
- [Exemplarische Vorgehensweise: Bearbeiten von Dateien und Verzeichnissen in Visual Basic](walkthrough-manipulating-files-and-directories.md)
- [Problembehandlung: Lesen aus und Schreiben in Textdateien](troubleshooting-reading-from-and-writing-to-text-files.md)
