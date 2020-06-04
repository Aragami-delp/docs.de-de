---
title: Entfernen von Elementen, Attributen und Knoten aus einem XML-Baum
ms.date: 07/20/2015
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
ms.openlocfilehash: f8be7fe521fb3c2662b105e34fd96fea1d1ac6e7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413405"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a><span data-ttu-id="a568c-102">Entfernen von Elementen, Attributen und Knoten aus einer XML-Struktur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a568c-102">Removing Elements, Attributes, and Nodes from an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="a568c-103">Sie können eine XML-Struktur ändern, indem Sie Elemente, Attribute und andere Knotentypen entfernen.</span><span class="sxs-lookup"><span data-stu-id="a568c-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>  
  
 <span data-ttu-id="a568c-104">Das Entfernen eines einzelnen Elements oder Attributs aus einem XML-Dokument ist unkompliziert.</span><span class="sxs-lookup"><span data-stu-id="a568c-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="a568c-105">Wenn Sie aber Auflistungen von Elementen oder Attributen entfernen, sollten Sie zuerst eine Auflistung in einer Liste materialisieren, bevor Sie die Elemente oder Attribute aus der Liste löschen.</span><span class="sxs-lookup"><span data-stu-id="a568c-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="a568c-106">Verwenden Sie dazu am besten die <xref:System.Xml.Linq.Extensions.Remove%2A>-Erweiterungsmethode, die diese Aufgabe für Sie übernimmt.</span><span class="sxs-lookup"><span data-stu-id="a568c-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>  
  
 <span data-ttu-id="a568c-107">Der Hauptgrund für diese Vorgehensweise besteht darin, dass die meisten Auflistungen, die Sie aus einer XML-Struktur abrufen, mit verzögerter Ausführung zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="a568c-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="a568c-108">Wenn Sie die Auflistungen nicht zunächst in einer Liste materialisieren oder wenn Sie nicht die Erweiterungsmethoden verwenden, kommt es möglicherweise zu einer bestimmten Form von Fehlern.</span><span class="sxs-lookup"><span data-stu-id="a568c-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="a568c-109">Weitere Informationen finden Sie unter [Fehler mit gemischtem deklarativem Code/imperativem Code (LINQ to XML) (Visual Basic)](mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a568c-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)](mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="a568c-110">Die folgenden Methoden entfernen Knoten und Attribute aus einer XML-Struktur.</span><span class="sxs-lookup"><span data-stu-id="a568c-110">The following methods remove nodes and attributes from an XML tree.</span></span>  
  
|<span data-ttu-id="a568c-111">Methode</span><span class="sxs-lookup"><span data-stu-id="a568c-111">Method</span></span>|<span data-ttu-id="a568c-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a568c-112">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="a568c-113">Entfernt einen <xref:System.Xml.Linq.XAttribute> aus seinem übergeordneten Knoten.</span><span class="sxs-lookup"><span data-stu-id="a568c-113">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="a568c-114">Entfernt die untergeordneten Knoten aus einem <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="a568c-114">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="a568c-115">Entfernt Inhalt und Attribute aus einem <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="a568c-115">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="a568c-116">Entfernt die Attribute eines <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="a568c-116">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="a568c-117">Entfernt das Attribut, wenn Sie als Wert `null` übergeben.</span><span class="sxs-lookup"><span data-stu-id="a568c-117">If you pass `null` for value, then removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="a568c-118">Entfernt das untergeordnete Element, wenn Sie als Wert `null` übergeben.</span><span class="sxs-lookup"><span data-stu-id="a568c-118">If you pass `null` for value, then removes the child element.</span></span>|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="a568c-119">Entfernt einen <xref:System.Xml.Linq.XNode> aus seinem übergeordneten Knoten.</span><span class="sxs-lookup"><span data-stu-id="a568c-119">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="a568c-120">Entfernt jedes Attribut oder Element in der Quellauflistung aus seinem übergeordneten Element.</span><span class="sxs-lookup"><span data-stu-id="a568c-120">Removes every attribute or element in the source collection from its parent element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a568c-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="a568c-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="a568c-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a568c-122">Description</span></span>  
 <span data-ttu-id="a568c-123">In diesem Beispiel werden drei Ansätze zum Entfernen von Elementen gezeigt.</span><span class="sxs-lookup"><span data-stu-id="a568c-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="a568c-124">Zuerst entfernt das Beispiel ein einzelnes Element.</span><span class="sxs-lookup"><span data-stu-id="a568c-124">First, it removes a single element.</span></span> <span data-ttu-id="a568c-125">Als Zweites ruft das Beispiel eine Auflistung von Elementen ab, materialisiert sie mit dem <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>-Operator und entfernt die Auflistung.</span><span class="sxs-lookup"><span data-stu-id="a568c-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="a568c-126">Zum Schluss ruft das Beispiel eine Auflistung von Elementen ab und entfernt diese mit der <xref:System.Xml.Linq.Extensions.Remove%2A>-Erweiterungsmethode.</span><span class="sxs-lookup"><span data-stu-id="a568c-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>  
  
 <span data-ttu-id="a568c-127">Weitere Informationen zum- <xref:System.Linq.Enumerable.ToList%2A> Operator finden Sie unter [Datentypen (Visual Basic)](converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="a568c-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (Visual Basic)](converting-data-types.md).</span></span>  
  
### <a name="code"></a><span data-ttu-id="a568c-128">Code</span><span class="sxs-lookup"><span data-stu-id="a568c-128">Code</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1/>  
            <GrandChild2/>  
            <GrandChild3/>  
        </Child1>  
        <Child2>  
            <GrandChild4/>  
            <GrandChild5/>  
            <GrandChild6/>  
        </Child2>  
        <Child3>  
            <GrandChild7/>  
            <GrandChild8/>  
            <GrandChild9/>  
        </Child3>  
    </Root>  
root.<Child1>.<GrandChild1>.Remove()  
root.<Child2>.Elements().ToList().Remove()  
root.<Child3>.Elements().Remove()  
Console.WriteLine(root)  
```  
  
### <a name="comments"></a><span data-ttu-id="a568c-129">Kommentare</span><span class="sxs-lookup"><span data-stu-id="a568c-129">Comments</span></span>  
 <span data-ttu-id="a568c-130">Dieser Code erzeugt die folgende Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="a568c-130">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>  
    <GrandChild2 />  
    <GrandChild3 />  
  </Child1>  
  <Child2 />  
  <Child3 />  
</Root>  
```  
  
 <span data-ttu-id="a568c-131">Beachten Sie, dass das erste Element der zweiten Unterebene aus `Child1` entfernt wurde.</span><span class="sxs-lookup"><span data-stu-id="a568c-131">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="a568c-132">Alle Elemente der zweiten Unterebene wurden aus `Child2` und `Child3` entfernt.</span><span class="sxs-lookup"><span data-stu-id="a568c-132">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a568c-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a568c-133">See also</span></span>

- [<span data-ttu-id="a568c-134">Ändern von XML-Strukturen (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a568c-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](modifying-xml-trees-linq-to-xml.md)
