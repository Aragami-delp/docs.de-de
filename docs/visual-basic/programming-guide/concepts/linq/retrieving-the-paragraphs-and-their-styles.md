---
title: Abrufen der Absätze und ihrer Stile
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: ad904abf9bd94e83b981859662c22787652e294f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413406"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a><span data-ttu-id="e0286-102">Abrufen der Absätze und ihrer Stile (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0286-102">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>
<span data-ttu-id="e0286-103">In diesem Beispiel schreiben wir eine Abfrage, die die Absatzknoten aus einem WordprocessingML-Dokument abruft.</span><span class="sxs-lookup"><span data-stu-id="e0286-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="e0286-104">Außerdem ermittelt es für jeden Absatz die verwendete Formatvorlage.</span><span class="sxs-lookup"><span data-stu-id="e0286-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="e0286-105">Diese Abfrage basiert auf der Abfrage im vorherigen Beispiel und [ermittelt die standardmäßige Absatzformat Vorlage (Visual Basic)](finding-the-default-paragraph-style.md), die den Standardstil aus der Liste der Stile abruft.</span><span class="sxs-lookup"><span data-stu-id="e0286-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="e0286-106">Diese Information wird benötigt, damit die Abfrage die Formatvorlagen der Absätze abrufen kann, für die keine Formatvorlage explizit festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="e0286-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="e0286-107">Absatzformatvorlagen werden über das `w:pPr`-Element festgelegt. Wenn ein Absatz dieses Element nicht enthält, wird er mit der Standardformatvorlage formatiert.</span><span class="sxs-lookup"><span data-stu-id="e0286-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="e0286-108">In diesem Thema wird die Bedeutung einiger Teile der Abfrage erläutert, bevor die Abfrage im Kontext eines vollständigen, funktionstüchtigen Beispiels gezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e0286-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0286-109">Beispiel</span><span class="sxs-lookup"><span data-stu-id="e0286-109">Example</span></span>  
 <span data-ttu-id="e0286-110">Die Abfrage verwendet zum Abrufen aller in einem Dokument vorhandenen Absätze und der zugehörigen Formatvorlagen die folgende Quelle:</span><span class="sxs-lookup"><span data-stu-id="e0286-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 <span data-ttu-id="e0286-111">Dieser Ausdruck ähnelt der Quelle der Abfrage im vorherigen Beispiel untersuchen [der standardmäßigen Absatzformat Vorlage (Visual Basic)](finding-the-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="e0286-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="e0286-112">Der Hauptunterschied besteht darin, dass der Ausdruck anstelle der <xref:System.Xml.Linq.XContainer.Descendants%2A>-Achse die <xref:System.Xml.Linq.XContainer.Elements%2A>-Achse verwendet.</span><span class="sxs-lookup"><span data-stu-id="e0286-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="e0286-113">Die Abfrage verwendet die <xref:System.Xml.Linq.XContainer.Descendants%2A>-Achse, weil in Dokumenten mit Abschnitten die Absätze nicht die direkten untergeordneten Elemente des Textkörpers sind. Die Absätze befinden sich zwei Ebenen weiter unten in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="e0286-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="e0286-114">Durch die Verwendung der <xref:System.Xml.Linq.XContainer.Descendants%2A>-Achse funktioniert der Code unabhängig davon, ob das Dokument Abschnitte verwendet.</span><span class="sxs-lookup"><span data-stu-id="e0286-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0286-115">Beispiel</span><span class="sxs-lookup"><span data-stu-id="e0286-115">Example</span></span>  
 <span data-ttu-id="e0286-116">Die Abfrage verwendet eine `Let`-Klausel, um das Element zu bestimmen, das den Formatvorlagenknoten enthält.</span><span class="sxs-lookup"><span data-stu-id="e0286-116">The query uses a `Let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="e0286-117">Wenn es kein Element gibt, wird `styleNode` auf `Nothing` gesetzt.</span><span class="sxs-lookup"><span data-stu-id="e0286-117">If there is no element, then `styleNode` is set to `Nothing`:</span></span>  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 <span data-ttu-id="e0286-118">Die `Let`-Klausel verwendet zuerst die <xref:System.Xml.Linq.XContainer.Elements%2A>-Achse, um nach allen Elementen mit dem Namen `pPr` zu suchen, und sucht dann mit der <xref:System.Xml.Linq.Extensions.Elements%2A>-Erweiterungsmethode nach allen untergeordneten Elementen mit dem Namen `pStyle`. Schließlich verwendet sie den <xref:System.Linq.Enumerable.FirstOrDefault%2A>-Standardabfrageoperator, um die Auflistung in ein Singleton umzuwandeln.</span><span class="sxs-lookup"><span data-stu-id="e0286-118">The `Let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="e0286-119">Wenn die Auflistung leer ist, wird `styleNode` auf `Nothing` gesetzt.</span><span class="sxs-lookup"><span data-stu-id="e0286-119">If the collection is empty, `styleNode` is set to `Nothing`.</span></span> <span data-ttu-id="e0286-120">Dies ist eine sinnvolle Vorgehensweise, um nach dem `pStyle`-Nachfolgerknoten zu suchen.</span><span class="sxs-lookup"><span data-stu-id="e0286-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="e0286-121">Beachten Sie dabei: Wenn der untergeordnete `pPr`-Knoten nicht existiert, löst der Code keine Ausnahme aus, sondern `styleNode` wird auf `Nothing` gesetzt, was dem erwünschten Verhalten dieser `Let`-Klausel entspricht.</span><span class="sxs-lookup"><span data-stu-id="e0286-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `Nothing`, which is the desired behavior of this `Let` clause.</span></span>  
  
 <span data-ttu-id="e0286-122">Die Abfrage projiziert eine Auflistung eines anonymen Typs mit zwei Membern, `StyleName` und `ParagraphNode`.</span><span class="sxs-lookup"><span data-stu-id="e0286-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0286-123">Beispiel</span><span class="sxs-lookup"><span data-stu-id="e0286-123">Example</span></span>  
 <span data-ttu-id="e0286-124">Dieses Beispiel verarbeitet ein WordprocessingML-Dokument, indem es die Absatzknoten aus einem WordprocessingML-Dokument abruft.</span><span class="sxs-lookup"><span data-stu-id="e0286-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="e0286-125">Außerdem ermittelt es für jeden Absatz die verwendete Formatvorlage.</span><span class="sxs-lookup"><span data-stu-id="e0286-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="e0286-126">Das Beispiel baut auf den vorherigen Beispielen dieses Lernprogramms auf.</span><span class="sxs-lookup"><span data-stu-id="e0286-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="e0286-127">Die neue Abfrage wird im Code unten durch entsprechende Kommentare gekennzeichnet.</span><span class="sxs-lookup"><span data-stu-id="e0286-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="e0286-128">Anweisungen zum Erstellen des Quelldokuments für dieses Beispiel finden Sie unter [Erstellen des Office Open XML-Quelldokuments (Visual Basic)](creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="e0286-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="e0286-129">Dieses Beispiel verwendet Klassen aus der <legacyBold>WindowsBase</legacyBold>-Assembly.</span><span class="sxs-lookup"><span data-stu-id="e0286-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="e0286-130">Außerdem werden Typen im <xref:System.IO.Packaging?displayProperty=nameWithType>-Namespace verwendet.</span><span class="sxs-lookup"><span data-stu-id="e0286-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    '  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        Dim defaultStyle As String = _  
            ( _  
                From style In styleDoc.Root.<w:style> _  
                Where style.@w:type = "paragraph" And _  
                      style.@w:default = "1" _  
                Select style _  
            ).First().@w:styleId  
  
        ' Following is the new query that finds all paragraphs in the  
        ' document and their styles.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault() _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        For Each p In paragraphs  
            Console.WriteLine("StyleName:{0}", p.StyleName)  
        Next  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="e0286-131">In diesem Beispiel wird die folgende Ausgabe erzeugt, wenn Sie auf das Dokument angewendet wird, [das unter Erstellen des Open XML-Quelldokuments (Visual Basic)](creating-the-source-office-open-xml-document.md)beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="e0286-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>  
  
```console  
StyleName:Heading1  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
```  
  
## <a name="next-steps"></a><span data-ttu-id="e0286-132">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="e0286-132">Next Steps</span></span>  
 <span data-ttu-id="e0286-133">Im nächsten Thema, [dem Abrufen des Texts der Absätze (Visual Basic)](retrieving-the-text-of-the-paragraphs.md), erstellen Sie eine Abfrage, um den Text von Absätzen abzurufen.</span><span class="sxs-lookup"><span data-stu-id="e0286-133">In the next topic, [Retrieving the Text of the Paragraphs (Visual Basic)](retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0286-134">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e0286-134">See also</span></span>

- [<span data-ttu-id="e0286-135">Tutorial: Bearbeiten von Inhalten in einem WordprocessingML-Dokument (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0286-135">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
