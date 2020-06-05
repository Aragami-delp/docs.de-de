---
title: 'Vorgehensweise: Ändern von XML-Literalen'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: a2ac2e9802d4c8ab522bb430d15cce5616430437
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374874"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a>Gewusst wie: Ändern von XML-Literalen (Visual Basic)

Visual Basic bietet bequeme Möglichkeiten zum Ändern von XML-Literalen. Sie können Elemente und Attribute hinzufügen oder löschen, und Sie können auch ein vorhandenes Element durch ein neues XML-Element ersetzen. Dieses Thema enthält mehrere Beispiele zum Ändern eines vorhandenen XML-Literals.

### <a name="to-modify-the-value-of-an-xml-literal"></a>So ändern Sie den Wert eines XML-Literals

1. Um den Wert eines XML-Literals zu ändern, rufen Sie einen Verweis auf das XML-wahrsten ab, und legen `Value` Sie die Eigenschaft auf den gewünschten Wert fest.

    Im folgenden Codebeispiel wird der Wert aller- \<Price> Elemente in einem XML-Dokument aktualisiert.

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    Das folgende Beispiel zeigt die XML-Beispieldatei und den geänderten XML-Code aus diesem Codebeispiel.

    Quell-XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    Geänderte XML-Daten:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>47.20</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>48.25</Price>
      </Book>
    </Catalog>
    ```

    > [!NOTE]
    > Die- `Value` Eigenschaft verweist auf das erste XML-Element in einer Auflistung. Wenn mehr als ein Element mit demselben Namen in einer Auflistung vorhanden ist, wirkt sich das Festlegen der `Value` Eigenschaft nur auf das erste Element in der Auflistung aus.

### <a name="to-add-an-attribute-to-an-xml-literal"></a>So fügen Sie einem XML-Literalattribut ein Attribut hinzu

1. Zum Hinzufügen eines Attributs zu einem XML-Literalwert rufen Sie zuerst einen Verweis auf das XML-Literale ab Anschließend können Sie ein Attribut hinzufügen, indem Sie eine neue XML-Attribut Achsen Eigenschaft hinzufügen. Sie können auch mit der-Methode ein neues- <xref:System.Xml.Linq.XAttribute> Objekt zum XML-Literaltyp hinzufügen <xref:System.Xml.Linq.XContainer.Add%2A> . Im folgenden Beispiel werden beide Optionen gezeigt.

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    Das folgende Beispiel zeigt die XML-Beispieldatei und den geänderten XML-Code aus diesem Codebeispiel.

    Quell-XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    Geänderte XML-Daten:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    Weitere Informationen zu Eigenschaften von XML-Attribut Achsen finden Sie unter [XML-Attribut Achsen Eigenschaft](../../../language-reference/xml-axis/xml-attribute-axis-property.md).

### <a name="to-add-an-element-to-an-xml-literal"></a>So fügen Sie einem XML-Literalelement ein Element hinzu

1. Um einem XML-Literalelement ein Element hinzuzufügen, müssen Sie zuerst einen Verweis auf das XML-Literalelement abrufen Anschließend können Sie mithilfe der-Methode ein neues- <xref:System.Xml.Linq.XElement> Objekt als letztes Unterelement des-Elements hinzufügen <xref:System.Xml.Linq.XContainer.Add%2A> . Mithilfe der-Methode können Sie ein neues- <xref:System.Xml.Linq.XElement> Objekt als erstes untergeordnetes Element hinzufügen <xref:System.Xml.Linq.XContainer.AddFirst%2A> .

    Wenn Sie ein neues Element an einer bestimmten Position relativ zu anderen untergeordneten Elementen hinzufügen möchten, rufen Sie zuerst einen Verweis auf ein benachbartes Unterelement ab. Anschließend können Sie das neue- <xref:System.Xml.Linq.XElement> Objekt vor dem angrenzenden Unterelement mithilfe der-Methode hinzufügen <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> . Sie können das neue- <xref:System.Xml.Linq.XElement> Objekt auch nach dem angrenzenden Unterelement mithilfe der-Methode hinzufügen <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> .

    Das folgende Beispiel zeigt Beispiele für jede dieser Techniken.

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    Das folgende Beispiel zeigt die XML-Beispieldatei und den geänderten XML-Code aus diesem Codebeispiel.

    Quell-XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    Geänderte XML-Daten:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331">
        <Publisher>Microsoft Press</Publisher>
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
        <PublishDate>2005-2-14</PublishDate>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a>So entfernen Sie ein Element oder Attribut aus einem XML-Literalelement

1. Wenn Sie ein Element oder Attribut aus einem XML-Literalzeichen entfernen möchten, rufen Sie einen Verweis auf das Element oder Attribut ab, und rufen Sie die- `Remove` Methode auf, wie im folgenden Beispiel gezeigt.

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    Das folgende Beispiel zeigt die XML-Beispieldatei und den geänderten XML-Code aus diesem Codebeispiel.

    Quell-XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

    Geänderte XML-Daten:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book></Catalog>
    ```

    Wenn Sie alle Elemente oder Attribute aus einem XML-Literalzeichen entfernen möchten, rufen Sie einen Verweis auf das XML-wahrsten ab, und rufen <xref:System.Xml.Linq.XElement.RemoveAll%2A> Sie die

### <a name="to-modify-an-xml-literal"></a>So ändern Sie ein XML-wahrsten

1. Um den Namen eines XML-Elements zu ändern, rufen Sie zuerst einen Verweis auf das Element ab. Sie können dann ein neues <xref:System.Xml.Linq.XElement> -Objekt mit einem neuen Namen erstellen und das neue- <xref:System.Xml.Linq.XElement> Objekt an die- <xref:System.Xml.Linq.XNode.ReplaceWith%2A> Methode des vorhandenen- <xref:System.Xml.Linq.XElement> Objekts übergeben.

    Wenn das Element, das Sie ersetzen, unter Elemente enthält, die beibehalten werden müssen, legen Sie den Wert des neuen- <xref:System.Xml.Linq.XElement> Objekts auf die- <xref:System.Xml.Linq.XContainer.Nodes%2A> Eigenschaft des vorhandenen Elements fest. Dadurch wird der Wert des neuen Elements auf den inneren XML-Code des vorhandenen Elements festgelegt. Andernfalls können Sie den Wert des neuen Elements auf die- `Value` Eigenschaft des vorhandenen-Elements festlegen.

    Im folgenden Codebeispiel werden alle- \<Description> Elemente durch ein- \<Abstract> Element ersetzt. Der Inhalt des- \<Description> Elements wird im neuen- \<Abstract> Element mithilfe der- <xref:System.Xml.Linq.XContainer.Nodes%2A> Eigenschaft des-Objekts beibehalten \<Description> <xref:System.Xml.Linq.XElement> .

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    Das folgende Beispiel zeigt die XML-Beispieldatei und den geänderten XML-Code aus diesem Codebeispiel.

    Quell-XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
        <Description>
          An in-depth look at creating applications
          with <technology>XML</technology>. For
          <audience>beginners</audience> or
          <audience>advanced</audience> developers.
        </Description>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
        <Description>
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Description>
      </Book>
    </Catalog>
    ```

    Geänderte XML-Daten:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <MSRP>44.95</MSRP>    <Abstract>
          An in-depth look at creating applications
          with <technology>XML</technology>. For
          <audience>beginners</audience> or
          <audience>advanced</audience> developers.
        </Abstract>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <MSRP>45.95</MSRP>    <Abstract>
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Abstract>
      </Book>
    </Catalog>
    ```

## <a name="see-also"></a>Weitere Informationen

- [Bearbeiten von XML in Visual Basic](manipulating-xml.md)
- [XML](index.md)
- [Vorgehensweise: Laden von XML aus einer Datei, einer Zeichenfolge oder einem Stream](how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../linq/index.md)
- [Einführung in LINQ in Visual Basic](../linq/introduction-to-linq.md)
