---
title: Erstellen eines Office Open-Quell-XML-Dokuments
ms.date: 07/20/2015
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
ms.openlocfilehash: 9f44c8d0f4080224c461736fdbdf3acd854e4a89
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410837"
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a>Erstellen des Office Open-Quell-XML-Dokuments (Visual Basic)
In diesem Thema wird das Erstellen des Office Open XML-WordprocessingML-Dokuments erläutert, das in den anderen Beispielen in diesem Lernprogramm verwendet wird. Wenn Sie diese Anweisungen befolgen, entspricht Ihre Ausgabe der Ausgabe im jeweiligen Beispiel.  
  
 Die Beispiele in diesem Lernprogramm funktionieren mit jedem gültigen WordprocessingML-Dokument.  
  
 Um das in diesem Tutorial verwendete Dokument erstellen zu können, muss bei Ihnen entweder Microsoft Office 2007 oder höher oder Microsoft Office 2003 mit dem Compatibility Pack für Microsoft Office 2007-Dateiformate installiert sein.  
  
## <a name="creating-the-wordprocessingml-document"></a>Erstellen des WordprocessingML-Dokuments  
  
#### <a name="to-create-the-wordprocessingml-document"></a>So erstellen Sie das WordprocessingML-Dokument  
  
1. Erstellen Sie ein neues Microsoft Word-Dokument.  
  
2. Fügen Sie in das neue Dokument den folgenden Text ein:  
  
    ```text  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    Imports System  
  
    Class Program  
        Public Shared  Sub Main(ByVal args() As String)  
            Console.WriteLine("Hello World")  
        End Sub  
    End Class  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3. Formatieren Sie die erste Zeile mit der Formatvorlage "Überschrift 1".  
  
4. Wählen Sie die Zeilen aus, die den Visual Basic Code enthalten. Die erste Zeile beginnt mit dem `Imports`-Schlüsselwort. Die letzte Zeile ist "End Class". Formatieren Sie die Zeilen mit der Schriftart Courier. Formatieren Sie sie anschließend mit einer neuen Formatvorlage, und geben Sie der neuen Formatvorlage den Namen "Code".  
  
5. Wählen Sie zum Schluss die gesamte Zeile aus, die die Ausgabe enthält, und formatieren Sie sie mit der `Code`-Formatvorlage.  
  
6. Speichern Sie das Dokument, und nennen Sie es <legacyBold>SampleDoc.docx</legacyBold>.  
  
    > [!NOTE]
    > Wenn Sie Microsoft Word 2003 verwenden, wählen Sie in der Dropdownliste **Dateityp** die Option **Word 2007-Dokument**.  
  
## <a name="see-also"></a>Weitere Informationen

- [Tutorial: Bearbeiten von Inhalten in einem WordprocessingML-Dokument (Visual Basic)](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
