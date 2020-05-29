---
title: 'Gewusst wie: Qualifizieren von XML-Element- und XML-Attributnamen'
description: In diesem Artikel wird gezeigt, wie Sie die Namen von XML-Elementen und XML-Attributen in XML-Dokumenten qualifizieren.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- qualifying XML names
- qualifying XML elements
- XML namespaces, qualifying elements and names in
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
ms.openlocfilehash: 6c29e03d9ce28e5b0abc68a5d7e8d82f4485ac93
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378414"
---
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a>Gewusst wie: Qualifizieren von XML-Element- und XML-Attributnamen

In Instanzen der <xref:System.Xml.Serialization.XmlSerializerNamespaces>-Klasse enthaltene XML-Namespaces müssen der Spezifikation [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/) des World Wide Web Consortium (W3C) entsprechen.

XML-Namespaces stellen eine Methode zur Qualifizierung der Namen von XML-Elementen und XML-Attributen in XML-Dokumenten bereit. Ein qualifizierter Name besteht aus einem Präfix und einem lokalen Namen, die durch einen Doppelpunkt voneinander getrennt sind. Das Präfix wird nur als Platzhalter verwendet und ist einem URI zugeordnet, der den Namespace angibt. Die Kombination aus dem global verwalteten URI-Namespace und dem lokalen Namen bildet einen weltweit garantiert eindeutigen Namen.

Sie können die in einem XML-Dokument verwendeten Präfixe festlegen, indem Sie eine Instanz von `XmlSerializerNamespaces` erstellen und die Namespacepaare dem Objekt hinzufügen.

## <a name="to-create-qualified-names-in-an-xml-document"></a>So erstellen Sie qualifizierte Namen in einem XML-Dokument

1. Erstellen Sie eine Instanz der `XmlSerializerNamespaces`-Klasse.

2. Fügen Sie alle Präfixe und Namespacepaare zu `XmlSerializerNamespaces` hinzu.

3. Wenden Sie das geeignete `System.Xml.Serialization`-Attribut auf jeden Member oder jede Klasse an, die von <xref:System.Xml.Serialization.XmlSerializer> in ein XML-Dokument serialisiert werden soll.

    Folgende Attribute sind verfügbar: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute> und <xref:System.Xml.Serialization.XmlTypeAttribute>.

4. Legen Sie die `Namespace`-Eigenschaft jedes Attributs auf einen der Namespacewerte aus dem `XmlSerializerNamespaces`-Objekt fest.

5. Übergeben Sie `XmlSerializerNamespaces` an die `Serialize`-Methode von `XmlSerializer`.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein `XmlSerializerNamespaces`-Objekt erstellt, dem zwei Paare aus Präfix und Namespace hinzugefügt werden. Durch den Code wird ein `XmlSerializer`-Objekt erstellt, das verwendet wird, um eine Instanz der `Books`-Klasse zu serialisieren. Im Code wird die `Serialize`-Methode mit `XmlSerializerNamespaces` aufgerufen. Der XML-Stream kann daher Namespaces mit Präfixen enthalten.

```vb
Imports System.IO
Imports System.Xml
Imports System.Xml.Serialization

Public Module Program

    Public Sub Main()
        SerializeObject("XmlNamespaces.xml")
    End Sub

    Public Sub SerializeObject(filename As String)
        Dim mySerializer As New XmlSerializer(GetType(Books))
        ' Writing a file requires a TextWriter.
        Dim myWriter As New StreamWriter(filename)

        ' Creates an XmlSerializerNamespaces and adds two
        ' prefix-namespace pairs.
        Dim myNamespaces As New XmlSerializerNamespaces()
        myNamespaces.Add("books", "http://www.cpandl.com")
        myNamespaces.Add("money", "http://www.cohowinery.com")

        ' Creates a Book.
        Dim myBook As New Book()
        myBook.TITLE = "A Book Title"
        Dim myPrice As New Price()
        myPrice.price = CDec(9.95)
        myPrice.currency = "US Dollar"
        myBook.PRICE = myPrice
        Dim myBooks As New Books()
        myBooks.Book = myBook
        mySerializer.Serialize(myWriter, myBooks, myNamespaces)
        myWriter.Close()
    End Sub
End Module

Public Class Books
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public Book As Book
End Class

<XmlType([Namespace] := "http://www.cpandl.com")> _
Public Class Book
    <XmlElement([Namespace] := "http://www.cpandl.com")> _
    Public TITLE As String
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public PRICE As Price
End Class

Public Class Price
    <XmlAttribute([Namespace] := "http://www.cpandl.com")> _
    Public currency As String
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public price As Decimal
End Class
```

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Serialization;

public class Program
{
    public static void Main()
    {
        SerializeObject("XmlNamespaces.xml");
    }

    public static void SerializeObject(string filename)
    {
        var mySerializer = new XmlSerializer(typeof(Books));
        // Writing a file requires a TextWriter.
        TextWriter myWriter = new StreamWriter(filename);

        // Creates an XmlSerializerNamespaces and adds two
        // prefix-namespace pairs.
        var myNamespaces = new XmlSerializerNamespaces();
        myNamespaces.Add("books", "http://www.cpandl.com");
        myNamespaces.Add("money", "http://www.cohowinery.com");

        // Creates a Book.
        var myBook = new Book();
        myBook.TITLE = "A Book Title";
        var myPrice = new Price();
        myPrice.price = (decimal) 9.95;
        myPrice.currency = "US Dollar";
        myBook.PRICE = myPrice;
        var myBooks = new Books();
        myBooks.Book = myBook;
        mySerializer.Serialize(myWriter, myBooks, myNamespaces);
        myWriter.Close();
    }
}

public class Books
{
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public Book Book;
}

[XmlType(Namespace ="http://www.cpandl.com")]
public class Book
{
    [XmlElement(Namespace = "http://www.cpandl.com")]
    public string TITLE;
    [XmlElement(Namespace ="http://www.cohowinery.com")]
    public Price PRICE;
}

public class Price
{
    [XmlAttribute(Namespace = "http://www.cpandl.com")]
    public string currency;
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public decimal price;
}
```

## <a name="see-also"></a>Siehe auch

- <xref:System.Xml.Serialization.XmlSerializer>
- [Das XML Schema Definition-Tool und die XML-Serialisierung](the-xml-schema-definition-tool-and-xml-serialization.md)
- [Einführung in die XML-Serialisierung](introducing-xml-serialization.md)
- [XmlSerializer-Klasse](xref:System.Xml.Serialization.XmlSerializer)
- [Attribute zur Steuerung der XML-Serialisierung](attributes-that-control-xml-serialization.md)
- [How to: Angeben eines alternativen Elementnamens für einen XML-Stream](how-to-specify-an-alternate-element-name-for-an-xml-stream.md).
- [How to: Serialisieren eines Objekts](how-to-serialize-an-object.md).
- [How to: Deserialisieren eines Objekts](how-to-deserialize-an-object.md).
