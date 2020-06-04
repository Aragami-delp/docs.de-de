---
title: Imports-Anweisung (XML-Namespace)
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: a3184d68b0e4cdff5d4296a5a638e22b4e83bcde
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404536"
---
# <a name="imports-statement-xml-namespace"></a><span data-ttu-id="6585e-102">Imports-Anweisung (XML-Namespace)</span><span class="sxs-lookup"><span data-stu-id="6585e-102">Imports Statement (XML Namespace)</span></span>

<span data-ttu-id="6585e-103">Importiert XML-Namespace Präfixe zur Verwendung in XML-Literalen und XML-Achsen Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="6585e-103">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="6585e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6585e-104">Syntax</span></span>

```vb
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">
```

## <a name="parts"></a><span data-ttu-id="6585e-105">Bestandteile</span><span class="sxs-lookup"><span data-stu-id="6585e-105">Parts</span></span>

`xmlNamespacePrefix`  
<span data-ttu-id="6585e-106">Optional.</span><span class="sxs-lookup"><span data-stu-id="6585e-106">Optional.</span></span> <span data-ttu-id="6585e-107">Die Zeichenfolge, auf die XML-Elemente und-Attribute verweisen können `xmlNamespaceName` .</span><span class="sxs-lookup"><span data-stu-id="6585e-107">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span></span> <span data-ttu-id="6585e-108">Wenn kein `xmlNamespacePrefix` angegeben wird, ist der importierte XML-Namespace der Standard-XML-Namespace.</span><span class="sxs-lookup"><span data-stu-id="6585e-108">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span></span> <span data-ttu-id="6585e-109">Muss ein gültiger XML-Bezeichner sein.</span><span class="sxs-lookup"><span data-stu-id="6585e-109">Must be a valid XML identifier.</span></span> <span data-ttu-id="6585e-110">Weitere Informationen finden Sie unter [Namen von deklarierten XML-Elementen und Attributen](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="6585e-110">For more information, see [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>

`xmlNamespaceName`  
<span data-ttu-id="6585e-111">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="6585e-111">Required.</span></span> <span data-ttu-id="6585e-112">Die Zeichenfolge, die den importierten XML-Namespace identifiziert.</span><span class="sxs-lookup"><span data-stu-id="6585e-112">The string identifying the XML namespace being imported.</span></span>

## <a name="remarks"></a><span data-ttu-id="6585e-113">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="6585e-113">Remarks</span></span>

<span data-ttu-id="6585e-114">Sie können die- `Imports` Anweisung verwenden, um globale XML-Namespaces zu definieren, die Sie mit XML-Literalen und XML-Achsen Eigenschaften verwenden können, oder als Parameter, die an den Operator weitergegeben werden `GetXmlNamespace` .</span><span class="sxs-lookup"><span data-stu-id="6585e-114">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="6585e-115">(Informationen zum Verwenden der- `Imports` Anweisung zum Importieren eines Alias, der verwendet werden kann, wo Typnamen in Ihrem Code verwendet werden, finden Sie unter [Imports-Anweisung (.NET-Namespace und-Typ)](imports-statement-net-namespace-and-type.md).) Die Syntax zum Deklarieren eines XML-Namespace mit der- `Imports` Anweisung ist identisch mit der Syntax, die in XML verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="6585e-115">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span></span> <span data-ttu-id="6585e-116">Daher können Sie eine Namespace Deklaration aus einer XML-Datei kopieren und in einer- `Imports` Anweisung verwenden.</span><span class="sxs-lookup"><span data-stu-id="6585e-116">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span></span>

<span data-ttu-id="6585e-117">XML-Namespace Präfixe sind nützlich, wenn Sie wiederholt XML-Elemente aus demselben Namespace erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="6585e-117">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span></span> <span data-ttu-id="6585e-118">Das mit der-Anweisung deklarierte XML-Namespace Präfix `Imports` ist in dem Sinn Global, dass es für den gesamten Code in der Datei verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="6585e-118">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span></span> <span data-ttu-id="6585e-119">Sie können Sie verwenden, wenn Sie XML-Element Literale erstellen und auf XML-Achsen Eigenschaften zugreifen.</span><span class="sxs-lookup"><span data-stu-id="6585e-119">You can use it when you create XML element literals and when you access XML axis properties.</span></span> <span data-ttu-id="6585e-120">Weitere Informationen finden Sie unter [XML-Elementliterale](../xml-literals/xml-element-literal.md) und [XML-Achsen Eigenschaften](../xml-axis/index.md).</span><span class="sxs-lookup"><span data-stu-id="6585e-120">For more information, see [XML Element Literal](../xml-literals/xml-element-literal.md) and [XML Axis Properties](../xml-axis/index.md).</span></span>

<span data-ttu-id="6585e-121">Wenn Sie einen globalen XML-Namespace ohne Namespace Präfix definieren (z. b `Imports <xmlns="http://SomeNameSpace>"` .), wird dieser Namespace als Standard-XML-Namespace betrachtet.</span><span class="sxs-lookup"><span data-stu-id="6585e-121">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span></span> <span data-ttu-id="6585e-122">Der Standard-XML-Namespace wird für alle XML-Element Literale oder XML-Attribut Achsen Eigenschaften verwendet, die nicht explizit einen Namespace angeben.</span><span class="sxs-lookup"><span data-stu-id="6585e-122">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span></span> <span data-ttu-id="6585e-123">Der Standard Namespace wird auch verwendet, wenn der angegebene Namespace der leere Namespace ist (d `xmlns=""` . h.).</span><span class="sxs-lookup"><span data-stu-id="6585e-123">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span></span> <span data-ttu-id="6585e-124">Der Standard-XML-Namespace gilt nicht für XML-Attribute in XML-Literalen oder XML-Attribut Achsen Eigenschaften, die keinen Namespace aufweisen.</span><span class="sxs-lookup"><span data-stu-id="6585e-124">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span></span>

<span data-ttu-id="6585e-125">XML-Namespaces, die in einem XML-Literaltyp definiert sind, die als *lokale XML-Namespaces*bezeichnet werden, haben Vorrang vor XML-Namespaces, die von der- `Imports` Anweisung als Global definiert werden.</span><span class="sxs-lookup"><span data-stu-id="6585e-125">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span></span> <span data-ttu-id="6585e-126">XML-Namespaces, die durch die-Anweisung definiert werden, haben `Imports` Vorrang vor XML-Namespaces, die für ein Visual Basic Projekt importiert werden.</span><span class="sxs-lookup"><span data-stu-id="6585e-126">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span></span> <span data-ttu-id="6585e-127">Wenn ein XML-Literale einen XML-Namespace definiert, gilt dieser lokale Namespace nicht für eingebettete Ausdrücke.</span><span class="sxs-lookup"><span data-stu-id="6585e-127">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span></span>

<span data-ttu-id="6585e-128">Globale XML-Namespaces befolgen dieselben Bereichs-und Definitions Regeln wie .NET Framework Namespaces.</span><span class="sxs-lookup"><span data-stu-id="6585e-128">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span></span> <span data-ttu-id="6585e-129">Daher können Sie eine- `Imports` Anweisung einschließen, um einen globalen XML-Namespace zu definieren, wo Sie einen .NET Framework-Namespace importieren können.</span><span class="sxs-lookup"><span data-stu-id="6585e-129">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span></span> <span data-ttu-id="6585e-130">Dies gilt sowohl für Code Dateien als auch für importierte Namespaces auf Projektebene.</span><span class="sxs-lookup"><span data-stu-id="6585e-130">This includes both code files and project-level imported namespaces.</span></span> <span data-ttu-id="6585e-131">Weitere Informationen zu importierten Namespaces auf Projektebene finden Sie unter [Seite "Verweise", Projekt-Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6585e-131">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>

<span data-ttu-id="6585e-132">Jede Quelldatei kann eine beliebige Anzahl von- `Imports` Anweisungen enthalten.</span><span class="sxs-lookup"><span data-stu-id="6585e-132">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="6585e-133">Diese müssen auf Options Deklarationen folgen, wie z. b. die `Option Strict` -Anweisung, und Sie müssen vor Programmierungs Element Deklarationen wie- `Module` oder-Anweisungen stehen `Class` .</span><span class="sxs-lookup"><span data-stu-id="6585e-133">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span></span>

## <a name="example"></a><span data-ttu-id="6585e-134">Beispiel</span><span class="sxs-lookup"><span data-stu-id="6585e-134">Example</span></span>

<span data-ttu-id="6585e-135">Im folgenden Beispiel werden ein Standard-XML-Namespace und ein XML-Namespace importiert, die mit dem Präfix identifiziert werden `ns` .</span><span class="sxs-lookup"><span data-stu-id="6585e-135">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span></span> <span data-ttu-id="6585e-136">Anschließend werden XML-Literale erstellt, die beide Namespaces verwenden.</span><span class="sxs-lookup"><span data-stu-id="6585e-136">It then creates XML literals that use both namespaces.</span></span>

[!code-vb[VbXMLSamples#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/Module1.vb#45)]

<span data-ttu-id="6585e-137">Durch diesen Code wird folgender Text angezeigt:</span><span class="sxs-lookup"><span data-stu-id="6585e-137">This code displays the following text:</span></span>

```xml
<ns:outer xmlns="http://DefaultNamespace"
          xmlns:ns="http://NewNamespace">
  <ns:innerElement></ns:innerElement>
  <siblingElement></siblingElement>
  <innerElement />
</ns:outer>
```

## <a name="example"></a><span data-ttu-id="6585e-138">Beispiel</span><span class="sxs-lookup"><span data-stu-id="6585e-138">Example</span></span>

<span data-ttu-id="6585e-139">Im folgenden Beispiel wird das XML-Namespace Präfix importiert `ns` .</span><span class="sxs-lookup"><span data-stu-id="6585e-139">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="6585e-140">Anschließend wird ein XML-wahrsten erstellt, das das Namespace Präfix verwendet und die endgültige Form des Elements anzeigt.</span><span class="sxs-lookup"><span data-stu-id="6585e-140">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="6585e-141">Durch diesen Code wird folgender Text angezeigt:</span><span class="sxs-lookup"><span data-stu-id="6585e-141">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="6585e-142">Beachten Sie, dass der Compiler das XML-Namespace Präfix aus einem globalen Präfix in eine lokale Präfix Definition konvertiert hat.</span><span class="sxs-lookup"><span data-stu-id="6585e-142">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span></span>

## <a name="example"></a><span data-ttu-id="6585e-143">Beispiel</span><span class="sxs-lookup"><span data-stu-id="6585e-143">Example</span></span>

<span data-ttu-id="6585e-144">Im folgenden Beispiel wird das XML-Namespace Präfix importiert `ns` .</span><span class="sxs-lookup"><span data-stu-id="6585e-144">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="6585e-145">Anschließend wird mit dem Namespacepräfix ein XML-Literal erstellt und auf den ersten untergeordneten Knoten mit dem qualifizierten Namen `ns:name` zugegriffen.</span><span class="sxs-lookup"><span data-stu-id="6585e-145">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]

<span data-ttu-id="6585e-146">Durch diesen Code wird folgender Text angezeigt:</span><span class="sxs-lookup"><span data-stu-id="6585e-146">This code displays the following text:</span></span>

`Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="6585e-147">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6585e-147">See also</span></span>

- [<span data-ttu-id="6585e-148">XML-Elementliteral</span><span class="sxs-lookup"><span data-stu-id="6585e-148">XML Element Literal</span></span>](../xml-literals/xml-element-literal.md)
- [<span data-ttu-id="6585e-149">XML-Achseneigenschaften</span><span class="sxs-lookup"><span data-stu-id="6585e-149">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="6585e-150">Namen von deklarierten XML-Elementen und Attributen</span><span class="sxs-lookup"><span data-stu-id="6585e-150">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="6585e-151">GetXmlNamespace-Operator</span><span class="sxs-lookup"><span data-stu-id="6585e-151">GetXmlNamespace Operator</span></span>](../operators/getxmlnamespace-operator.md)
