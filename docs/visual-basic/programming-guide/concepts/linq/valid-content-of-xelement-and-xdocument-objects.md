---
title: Gültiger Inhalt von XElement-und XDocument-Objects2
ms.date: 07/20/2015
ms.assetid: 400bb692-478a-40b6-ac1b-4ccbb4cbbd02
ms.openlocfilehash: d222f19f6f588968a3ef1515dca522a4a80e1ffb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364343"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="7f7cd-102">Gültiger Inhalt von XElement- und XDocument-Objekten</span><span class="sxs-lookup"><span data-stu-id="7f7cd-102">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="7f7cd-103">In diesem Thema werden die gültigen Argumente beschrieben, die an die Konstruktoren und Methoden übergeben werden können, die Sie zum Hinzufügen von Inhalt zu Elementen und Dokumenten verwenden.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-103">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="7f7cd-104">Gültiger Inhalt</span><span class="sxs-lookup"><span data-stu-id="7f7cd-104">Valid Content</span></span>  
 <span data-ttu-id="7f7cd-105">Abfragen ergeben häufig <xref:System.Collections.Generic.IEnumerable%601> für <xref:System.Xml.Linq.XElement> oder <xref:System.Collections.Generic.IEnumerable%601> für <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-105">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="7f7cd-106">Sie können Auflistungen mit <xref:System.Xml.Linq.XElement>- oder <xref:System.Xml.Linq.XAttribute>-Objekten an den <xref:System.Xml.Linq.XElement>-Konstruktor übergeben.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-106">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="7f7cd-107">Aus diesem Grund bietet es sich an, die Ergebnisse einer Abfrage als Inhalt an Methoden und Konstruktoren zu übergeben, mit denen Sie XML-Strukturen auffüllen können.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-107">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="7f7cd-108">Beim Hinzufügen einfachen Inhalts können dieser Methode verschiedene Typen übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-108">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="7f7cd-109">Gültige Typen sind:</span><span class="sxs-lookup"><span data-stu-id="7f7cd-109">Valid types include the following:</span></span>  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- <span data-ttu-id="7f7cd-110">Alle Typen, die `Object.ToString` implementieren.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-110">Any type that implements `Object.ToString`.</span></span>  
  
- <span data-ttu-id="7f7cd-111">Alle Typen, die <xref:System.Collections.Generic.IEnumerable%601> implementieren.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-111">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="7f7cd-112">Beim Hinzufügen komplexen Inhalts können an diese Methode verschiedene Typen übergeben werden:</span><span class="sxs-lookup"><span data-stu-id="7f7cd-112">When adding complex content, various types can be passed to this method:</span></span>  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- <span data-ttu-id="7f7cd-113">Jeder Typ, der <xref:System.Collections.Generic.IEnumerable%601> implementiert</span><span class="sxs-lookup"><span data-stu-id="7f7cd-113">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="7f7cd-114">Wenn ein Objekt eine <xref:System.Collections.Generic.IEnumerable%601> implementiert, wird die Auflistung im Objekt aufgezählt, und alle Elemente in der Auflistung werden hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-114">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="7f7cd-115">Wenn die Auflistung <xref:System.Xml.Linq.XNode>-Objekte oder <xref:System.Xml.Linq.XAttribute>-Objekte enthält, wird jedes Element in der Auflistung getrennt hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-115">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="7f7cd-116">Wenn die Auflistung Text (oder Objekte, die in Text umgewandelt wurden) enthält, wird der Text in der Auflistung verkettet und als einzelner Textknoten hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-116">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="7f7cd-117">Wenn der Inhalt `null` ist, wird nichts hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-117">If content is `null`, nothing is added.</span></span> <span data-ttu-id="7f7cd-118">Bei der Übergabe einer Auflistung können Elemente der Auflistung `null` sein.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-118">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="7f7cd-119">Ein `null`-Element in der Auflistung hat keine Auswirkungen auf die Struktur.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-119">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="7f7cd-120">Ein hinzugefügtes Attribut muss innerhalb des Elements, in dem es enthalten ist, einen eindeutigen Namen besitzen.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-120">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="7f7cd-121">Wenn der neue Inhalt beim Hinzufügen von <xref:System.Xml.Linq.XNode>-Objekten oder <xref:System.Xml.Linq.XAttribute>-Objekten kein übergeordnetes Element besitzt, werden die Objekte einfach an die XML-Struktur angefügt.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-121">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="7f7cd-122">Wenn der neue Inhalt bereits ein übergeordnetes Element besitzt und Bestandteil einer anderen XML-Struktur ist, wird der neue Inhalt geklont, und der neu geklonte Inhalt wird an die XML-Struktur angefügt.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-122">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="7f7cd-123">Gültiger Inhalt für Dokumente</span><span class="sxs-lookup"><span data-stu-id="7f7cd-123">Valid Content for Documents</span></span>  
 <span data-ttu-id="7f7cd-124">Es ist nicht möglich, einem Dokument Attribute und einfachen Inhalt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-124">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="7f7cd-125">Die Anzahl der Szenarios, in denen Sie ein <xref:System.Xml.Linq.XDocument> erstellen müssen, ist sehr begrenzt.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-125">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="7f7cd-126">Stattdessen können Sie i. d. R. die XML-Strukturen mit einem <xref:System.Xml.Linq.XElement>-Stammknoten erstellen.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-126">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="7f7cd-127">Sofern es keine bestimmte Anforderung für das Erstellen eines Dokuments gibt (z. B., weil Sie Verarbeitungsanweisungen und Kommentare auf der obersten Ebene erstellen oder Dokumenttypen unterstützen müssen), ist es oft bequemer, <xref:System.Xml.Linq.XElement> als Stammknoten zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-127">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="7f7cd-128">Als gültiger Inhalt für Dokumente gilt z. B.:</span><span class="sxs-lookup"><span data-stu-id="7f7cd-128">Valid content for a document includes the following:</span></span>  
  
- <span data-ttu-id="7f7cd-129">kein oder ein <xref:System.Xml.Linq.XDocumentType>-Objekt:</span><span class="sxs-lookup"><span data-stu-id="7f7cd-129">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="7f7cd-130">Die Dokumenttypen müssen vor dem Element kommen.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-130">The document types must come before the element.</span></span>  
  
- <span data-ttu-id="7f7cd-131">kein oder ein Element</span><span class="sxs-lookup"><span data-stu-id="7f7cd-131">Zero or one element.</span></span>  
  
- <span data-ttu-id="7f7cd-132">keine oder mehrere Kommentare</span><span class="sxs-lookup"><span data-stu-id="7f7cd-132">Zero or more comments.</span></span>  
  
- <span data-ttu-id="7f7cd-133">keine oder mehrere Verarbeitungsanweisungen</span><span class="sxs-lookup"><span data-stu-id="7f7cd-133">Zero or more processing instructions.</span></span>  
  
- <span data-ttu-id="7f7cd-134">keine oder mehrere Textknoten, die nur Leerraum enthalten</span><span class="sxs-lookup"><span data-stu-id="7f7cd-134">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="7f7cd-135">Konstruktoren und Funktionen, die das Hinzufügen von Inhalt erlauben</span><span class="sxs-lookup"><span data-stu-id="7f7cd-135">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="7f7cd-136">Die folgenden Methoden ermöglichen es Ihnen, einem <xref:System.Xml.Linq.XElement>-Objekt oder <xref:System.Xml.Linq.XDocument>-Objekt untergeordneten Inhalt hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="7f7cd-136">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="7f7cd-137">Methode</span><span class="sxs-lookup"><span data-stu-id="7f7cd-137">Method</span></span>|<span data-ttu-id="7f7cd-138">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="7f7cd-138">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="7f7cd-139">Konstruiert ein <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-139">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="7f7cd-140">Erstellt ein Objekt vom Typ <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-140">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="7f7cd-141">Fügt Inhalt am Ende des untergeordneten Inhalts des <xref:System.Xml.Linq.XElement>- oder <xref:System.Xml.Linq.XDocument>-Objekts hinzu.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-141">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="7f7cd-142">Fügt Inhalt nach dem <xref:System.Xml.Linq.XNode> hinzu.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-142">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="7f7cd-143">Fügt Inhalt vor dem <xref:System.Xml.Linq.XNode> hinzu.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-143">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="7f7cd-144">Fügt Inhalt vor dem untergeordneten Inhalt des <xref:System.Xml.Linq.XContainer> hinzu.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-144">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="7f7cd-145">Ersetzt den gesamten Inhalt (untergeordnete Knoten und Attribute) eines <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-145">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="7f7cd-146">Ersetzt die Attribute eines <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-146">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="7f7cd-147">Ersetzt die untergeordneten Knoten durch neuen Inhalt.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-147">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="7f7cd-148">Ersetzt einen Knoten durch neuen Inhalt.</span><span class="sxs-lookup"><span data-stu-id="7f7cd-148">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f7cd-149">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7f7cd-149">See also</span></span>

- [<span data-ttu-id="7f7cd-150">Erstellen von XML-Strukturen (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f7cd-150">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)
