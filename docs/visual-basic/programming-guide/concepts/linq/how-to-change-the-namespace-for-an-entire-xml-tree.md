---
title: 'Vorgehensweise: Ändern des Namespaces für eine vollständige XML-Struktur'
ms.date: 07/20/2015
ms.assetid: 1837324b-5cb5-4fa8-95b9-3071efa0f913
ms.openlocfilehash: 11938b575ed5133d930e585dbe4d744e3168cced
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374978"
---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-visual-basic"></a><span data-ttu-id="b2bb8-102">Vorgehensweise: Ändern des Namespaces für eine gesamte XML-Struktur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2bb8-102">How to: Change the Namespace for an Entire XML Tree (Visual Basic)</span></span>
<span data-ttu-id="b2bb8-103">Es kann passieren, dass Sie den Namespace für ein Element oder Attribut programmgesteuert ändern müssen.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-103">You sometimes have to programmatically change the namespace for an element or an attribute.</span></span> <span data-ttu-id="b2bb8-104">Mit LINQ to XML ist dies ganz einfach.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-104">LINQ to XML makes this easy.</span></span> <span data-ttu-id="b2bb8-105">Sie können die <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType>-Eigenschaft festlegen.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-105">The <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> property can be set.</span></span> <span data-ttu-id="b2bb8-106">Die <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType>-Eigenschaft kann nicht festgelegt werden, Sie können aber problemlos die Attribute in eine <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> kopieren, die vorhandenen Attribute entfernen und dann neue Attribute hinzufügen, die sich im neuen gewünschten Namespace befinden.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-106">The <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> property cannot be set, but you can easily copy the attributes into a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, remove the existing attributes, and then add new attributes that are in the new desired namespace.</span></span>  
  
 <span data-ttu-id="b2bb8-107">Weitere Informationen finden Sie unter [Übersicht über Namespaces (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b2bb8-107">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2bb8-108">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b2bb8-108">Example</span></span>  
 <span data-ttu-id="b2bb8-109">Der folgende Code erstellt zwei XML-Strukturen, die sich in keinem Namespace befinden.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-109">The following code creates two XML trees in no namespace.</span></span> <span data-ttu-id="b2bb8-110">Er ändert dann den Namespace beider Strukturen und fasst die Strukturen in einer gemeinsamen Struktur zusammen.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-110">It then changes the namespace of each of the trees, and combines them into a single tree.</span></span>  
  
```vb  
Dim tree1 As XElement = _  
    <Data>  
        <Child MyAttr="content">content</Child>  
    </Data>  
Dim tree2 As XElement = _  
    <Data>  
        <Child MyAttr="content">content</Child>  
    </Data>  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim ad As XNamespace = "http://www.adatum.com"  
' change the namespace of every element and attribute in the first tree  
For Each el As XElement In tree1.DescendantsAndSelf  
    el.Name = aw.GetName(el.Name.LocalName)  
    Dim atList As List(Of XAttribute) = el.Attributes().ToList()  
    el.Attributes().Remove()  
    For Each at As XAttribute In atList  
        el.Add(New XAttribute(aw.GetName(at.Name.LocalName), at.Value))  
    Next  
Next  
' change the namespace of every element and attribute in the second tree  
For Each el As XElement In tree2.DescendantsAndSelf()  
    el.Name = ad.GetName(el.Name.LocalName)  
    Dim atList As List(Of XAttribute) = el.Attributes().ToList()  
    el.Attributes().Remove()  
    For Each at As XAttribute In atList  
        el.Add(New XAttribute(ad.GetName(at.Name.LocalName), at.Value))  
    Next  
Next  
' add attribute namespaces so that the tree will be serialized with  
' the aw and ad namespace prefixes  
tree1.Add( _  
    New XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com") _  
)  
tree2.Add( _  
    New XAttribute(XNamespace.Xmlns + "ad", "http://www.adatum.com") _  
)  
' create a new composite tree  
Dim root As XElement = _  
    <Root>  
        <%= tree1 %>  
        <%= tree2 %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="b2bb8-111">Dieses Beispiel erzeugt die folgende Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <aw:Data xmlns:aw="http://www.adventure-works.com">  
    <aw:Child aw:MyAttr="content">content</aw:Child>  
  </aw:Data>  
  <ad:Data xmlns:ad="http://www.adatum.com">  
    <ad:Child ad:MyAttr="content">content</ad:Child>  
  </ad:Data>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2bb8-112">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b2bb8-112">See also</span></span>

- [<span data-ttu-id="b2bb8-113">Ändern von XML-Strukturen (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2bb8-113">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](modifying-xml-trees-linq-to-xml.md)
