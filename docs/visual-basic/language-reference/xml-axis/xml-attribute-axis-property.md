---
title: XML Attribute Axis Property
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
ms.openlocfilehash: 3f60190a949856cb2bbc2eba09d097c09089bea7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408431"
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="f6686-102">XML-Attributachseneigenschaft (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6686-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="f6686-103">Bietet Zugriff auf den Wert eines Attributs für ein <xref:System.Xml.Linq.XElement> Objekt oder auf das erste Element in einer Auflistung von- <xref:System.Xml.Linq.XElement> Objekten.</span><span class="sxs-lookup"><span data-stu-id="f6686-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6686-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f6686-104">Syntax</span></span>  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="f6686-105">Bestandteile</span><span class="sxs-lookup"><span data-stu-id="f6686-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="f6686-106">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f6686-106">Required.</span></span> <span data-ttu-id="f6686-107">Ein- <xref:System.Xml.Linq.XElement> Objekt oder eine Auflistung von- <xref:System.Xml.Linq.XElement> Objekten.</span><span class="sxs-lookup"><span data-stu-id="f6686-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="f6686-108">.@</span><span class="sxs-lookup"><span data-stu-id="f6686-108">.@</span></span>  
 <span data-ttu-id="f6686-109">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f6686-109">Required.</span></span> <span data-ttu-id="f6686-110">Gibt den Anfang einer Attribut Achsen Eigenschaft an.</span><span class="sxs-lookup"><span data-stu-id="f6686-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="f6686-111">Optional.</span><span class="sxs-lookup"><span data-stu-id="f6686-111">Optional.</span></span> <span data-ttu-id="f6686-112">Gibt den Anfang des Namens des Attributs an, wenn `attribute` in Visual Basic kein gültiger Bezeichner ist.</span><span class="sxs-lookup"><span data-stu-id="f6686-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
 `attribute`  
 <span data-ttu-id="f6686-113">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f6686-113">Required.</span></span> <span data-ttu-id="f6686-114">Der Name des Attributs, auf das im Format [ `prefix` :] zugegriffen werden soll `name` .</span><span class="sxs-lookup"><span data-stu-id="f6686-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="f6686-115">Teil</span><span class="sxs-lookup"><span data-stu-id="f6686-115">Part</span></span>|<span data-ttu-id="f6686-116">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="f6686-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="f6686-117">Optional.</span><span class="sxs-lookup"><span data-stu-id="f6686-117">Optional.</span></span> <span data-ttu-id="f6686-118">Das XML-Namespace Präfix für das Attribut.</span><span class="sxs-lookup"><span data-stu-id="f6686-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="f6686-119">Muss ein globaler XML-Namespace sein, der mit einer `Imports`-Anweisung definiert ist.</span><span class="sxs-lookup"><span data-stu-id="f6686-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="f6686-120">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f6686-120">Required.</span></span> <span data-ttu-id="f6686-121">Name des lokalen Attributs.</span><span class="sxs-lookup"><span data-stu-id="f6686-121">Local attribute name.</span></span> <span data-ttu-id="f6686-122">Siehe [Namen von deklarierten XML-Elementen und Attributen](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="f6686-122">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="f6686-123">Optional.</span><span class="sxs-lookup"><span data-stu-id="f6686-123">Optional.</span></span> <span data-ttu-id="f6686-124">Bezeichnet das Ende des Namens des Attributs, wenn `attribute` kein gültiger Bezeichner in Visual Basic ist.</span><span class="sxs-lookup"><span data-stu-id="f6686-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6686-125">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="f6686-125">Return Value</span></span>  
 <span data-ttu-id="f6686-126">Eine Zeichenfolge, die den Wert von enthält `attribute` .</span><span class="sxs-lookup"><span data-stu-id="f6686-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="f6686-127">Wenn der Attribut Name nicht vorhanden ist, `Nothing` wird zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="f6686-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6686-128">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="f6686-128">Remarks</span></span>  
 <span data-ttu-id="f6686-129">Sie können eine XML-Attribut Achsen Eigenschaft verwenden, um auf den Wert eines Attributs anhand des Namens aus einem <xref:System.Xml.Linq.XElement> Objekt oder aus dem ersten Element in einer Auflistung von- <xref:System.Xml.Linq.XElement> Objekten zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="f6686-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="f6686-130">Sie können einen Attribut Wert anhand des Namens abrufen oder einem Element ein neues Attribut hinzufügen, indem Sie einen neuen Namen mit vorangestelltem @-Bezeichner angeben.</span><span class="sxs-lookup"><span data-stu-id="f6686-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="f6686-131">Wenn Sie auf ein XML-Attribut mit dem @-Bezeichner verweisen, wird der-Attribut Wert als Zeichenfolge zurückgegeben, und Sie müssen die-Eigenschaft nicht explizit angeben <xref:System.Xml.Linq.XAttribute.Value%2A> .</span><span class="sxs-lookup"><span data-stu-id="f6686-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="f6686-132">Die Benennungs Regeln für XML-Attribute unterscheiden sich von den Benennungs Regeln für Visual Basic Bezeichner.</span><span class="sxs-lookup"><span data-stu-id="f6686-132">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span></span> <span data-ttu-id="f6686-133">Um auf ein XML-Attribut zuzugreifen, das über einen Namen verfügt, der kein gültiger Visual Basic Bezeichner ist, müssen Sie den Namen in spitzen Klammern ( \< and > ) einschließen.</span><span class="sxs-lookup"><span data-stu-id="f6686-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="f6686-134">XML-Namespaces</span><span class="sxs-lookup"><span data-stu-id="f6686-134">XML Namespaces</span></span>  
 <span data-ttu-id="f6686-135">Der Name in einer Attribut Achsen Eigenschaft kann nur XML-Namespace Präfixe verwenden, die Global mithilfe der-Anweisung deklariert werden `Imports` .</span><span class="sxs-lookup"><span data-stu-id="f6686-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="f6686-136">Es können keine XML-Namespacepräfixe verwendet werden, die lokal innerhalb von XML-Elementliteralen deklariert wurden.</span><span class="sxs-lookup"><span data-stu-id="f6686-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="f6686-137">Weitere Informationen finden Sie unter [Imports-Anweisung (XML-Namespace)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="f6686-137">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6686-138">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f6686-138">Example</span></span>  
 <span data-ttu-id="f6686-139">Im folgenden Beispiel wird gezeigt, wie Sie die Werte der XML-Attribute aus einer Auflistung von XML-Elementen mit dem Namen "" `type` aus einer Auflistung von XML-Elementen `phone`</span><span class="sxs-lookup"><span data-stu-id="f6686-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 <span data-ttu-id="f6686-140">Durch diesen Code wird folgender Text angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f6686-140">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="f6686-141">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f6686-141">Example</span></span>  
 <span data-ttu-id="f6686-142">Im folgenden Beispiel wird gezeigt, wie Attribute für ein XML-Element sowohl deklarativ als auch als Teil des XML-Codes erstellt werden, und dynamisch durch Hinzufügen eines Attributs zu einer Instanz eines <xref:System.Xml.Linq.XElement> Objekts.</span><span class="sxs-lookup"><span data-stu-id="f6686-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="f6686-143">Das `type` Attribut wird deklarativ erstellt, und das `owner` Attribut wird dynamisch erstellt.</span><span class="sxs-lookup"><span data-stu-id="f6686-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 <span data-ttu-id="f6686-144">Durch diesen Code wird folgender Text angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f6686-144">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="f6686-145">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f6686-145">Example</span></span>  
 <span data-ttu-id="f6686-146">Im folgenden Beispiel wird die Spitze Klammer Syntax verwendet, um den Wert des XML-Attributs mit dem Namen zu erhalten `number-type` , der kein gültiger Bezeichner in Visual Basic ist.</span><span class="sxs-lookup"><span data-stu-id="f6686-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span></span>  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 <span data-ttu-id="f6686-147">Durch diesen Code wird folgender Text angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f6686-147">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="f6686-148">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f6686-148">Example</span></span>  
 <span data-ttu-id="f6686-149">Das folgende Beispiel deklariert `ns` als ein XML-Namespacepräfix.</span><span class="sxs-lookup"><span data-stu-id="f6686-149">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="f6686-150">Anschließend wird das Präfix des-Namespace verwendet, um ein XML-Literalelement zu erstellen und auf den ersten untergeordneten Knoten mit dem qualifizierten Namen " `ns:name` " zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="f6686-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 <span data-ttu-id="f6686-151">Durch diesen Code wird folgender Text angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f6686-151">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="f6686-152">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f6686-152">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="f6686-153">XML-Achseneigenschaften</span><span class="sxs-lookup"><span data-stu-id="f6686-153">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="f6686-154">XML-Literale</span><span class="sxs-lookup"><span data-stu-id="f6686-154">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="f6686-155">Erstellen von XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f6686-155">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="f6686-156">Namen von deklarierten XML-Elementen und Attributen</span><span class="sxs-lookup"><span data-stu-id="f6686-156">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
