---
title: 'Vorgehensweise: Lesen und Schreiben eines codierten Dokuments'
ms.date: 07/20/2015
ms.assetid: 159d868f-5ac8-40f2-95ca-07dd925f35c6
ms.openlocfilehash: f66737429950e04f447dfbd58cf47b6434a22976
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397907"
---
# <a name="how-to-read-and-write-an-encoded-document-visual-basic"></a>Vorgehensweise: Lesen und Schreiben eines codierten Dokuments (Visual Basic)

Fügen Sie zum Erstellen eines codierten XML-Dokuments der XML-Struktur eine <xref:System.Xml.Linq.XDeclaration> hinzu, die die Codierung auf den gewünschten Codeseitennamen festlegt.

Jeder von <xref:System.Text.Encoding.WebName%2A> zurückgegebene Wert ist ein gültiger Wert.

Beim Lesen eines codierten Dokuments wird die <xref:System.Xml.Linq.XDeclaration.Encoding%2A>-Eigenschaft auf den Codeseitennamen festgelegt.

Wenn Sie die <xref:System.Xml.Linq.XDeclaration.Encoding%2A> auf einen gültigen Codeseitennamen festgelegt haben, verwendet [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zum Serialisieren die angegebene Codierung.

## <a name="example"></a>Beispiel

Das folgende Beispiel erstellt zwei Dokumente: eines mit UTF-8-Codierung und eines mit UTF-16-Codierung. Anschließend werden die Dokumente geladen, und die Codierung wird auf der Konsole ausgegeben.

```vb
Console.WriteLine("Creating a document with utf-8 encoding")
Dim encodedDoc8 As XDocument = _
        <?xml version='1.0' encoding='utf-8' standalone='yes'?>
        <Root>Content</Root>

encodedDoc8.Save("EncodedUtf8.xml")
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding)
Console.WriteLine()

Console.WriteLine("Creating a document with utf-16 encoding")
Dim encodedDoc16 As XDocument = _
        <?xml version='1.0' encoding='utf-16' standalone='yes'?>
        <Root>Content</Root>

encodedDoc16.Save("EncodedUtf16.xml")
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding)
Console.WriteLine()

Dim newDoc8 As XDocument = XDocument.Load("EncodedUtf8.xml")
Console.WriteLine("Encoded document:")
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"))
Console.WriteLine()
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding)
Console.WriteLine()

Dim newDoc16 As XDocument = XDocument.Load("EncodedUtf16.xml")
Console.WriteLine("Encoded document:")
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"))
Console.WriteLine()
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding)
```

Dieses Beispiel erzeugt die folgende Ausgabe:

```console
Creating a document with utf-8 encoding
Encoding is:utf-8

Creating a document with utf-16 encoding
Encoding is:utf-16

Encoded document:
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Root>Content</Root>

Encoding of loaded document is:utf-8

Encoded document:
<?xml version="1.0" encoding="utf-16" standalone="yes"?>
<Root>Content</Root>

Encoding of loaded document is:utf-16
```

## <a name="see-also"></a>Weitere Informationen

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
- [Erweiterte LINQ to XML Programmierung (Visual Basic)](advanced-linq-to-xml-programming.md)
