---
title: x:Type-Markuperweiterung
ms.date: 03/30/2017
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
ms.openlocfilehash: f75d4e30dc41bbce995e466466c96c1a2830949b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2020
ms.locfileid: "81432635"
---
# <a name="xtype-markup-extension"></a><span data-ttu-id="fca71-102">x:Type-Markuperweiterung</span><span class="sxs-lookup"><span data-stu-id="fca71-102">x:Type Markup Extension</span></span>

<span data-ttu-id="fca71-103">Stellt das <xref:System.Type> CLR-Objekt an, das der zugrunde liegende Typ für einen angegebenen XAML-Typ ist.</span><span class="sxs-lookup"><span data-stu-id="fca71-103">Supplies the CLR <xref:System.Type> object that is the underlying type for a specified XAML type.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="fca71-104">Verwendung von XAML-Attributen</span><span class="sxs-lookup"><span data-stu-id="fca71-104">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Type prefix:typeNameValue}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="fca71-105">Verwendung von XAML-Objektelementen</span><span class="sxs-lookup"><span data-stu-id="fca71-105">XAML Object Element Usage</span></span>

```xaml
<x:Type TypeName="prefix:typeNameValue"/>
```

## <a name="xaml-values"></a><span data-ttu-id="fca71-106">XAML-Werte</span><span class="sxs-lookup"><span data-stu-id="fca71-106">XAML Values</span></span>

|||
|-|-|
|`prefix`|<span data-ttu-id="fca71-107">Optional.</span><span class="sxs-lookup"><span data-stu-id="fca71-107">Optional.</span></span> <span data-ttu-id="fca71-108">Ein Präfix, das einen nicht standardmäßigen XAML-Namespace zuordnet.</span><span class="sxs-lookup"><span data-stu-id="fca71-108">A prefix that maps a non-default XAML namespace.</span></span> <span data-ttu-id="fca71-109">Die Angabe eines Präfixes ist häufig nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="fca71-109">Specifying a prefix is frequently not necessary.</span></span> <span data-ttu-id="fca71-110">Siehe Hinweise.</span><span class="sxs-lookup"><span data-stu-id="fca71-110">See Remarks.</span></span>|
|`typeNameValue`|<span data-ttu-id="fca71-111">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="fca71-111">Required.</span></span> <span data-ttu-id="fca71-112">Ein Typname, der auf den aktuellen Standard-XAML-Namespace aufgelöst werden kann. oder das angegebene zugeordnete `prefix` Präfix, wenn angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="fca71-112">A type name resolvable to the current default XAML namespace; or the specified mapped prefix if `prefix` is supplied.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fca71-113">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="fca71-113">Remarks</span></span>

<span data-ttu-id="fca71-114">Die `x:Type` Markuperweiterung hat eine `typeof()` ähnliche Funktion wie `GetType` der Operator in C- oder der Operator in Microsoft Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fca71-114">The `x:Type` markup extension has a similar function to the `typeof()` operator in C# or the `GetType` operator in Microsoft Visual Basic.</span></span>

<span data-ttu-id="fca71-115">Die `x:Type` Markuperweiterung stellt ein Konvertierungsverhalten von aus <xref:System.Type>der Zeichenfolge für Eigenschaften zur Verfügung, die den Typ annehmen.</span><span class="sxs-lookup"><span data-stu-id="fca71-115">The `x:Type` markup extension supplies a from-string conversion behavior for properties that take the type <xref:System.Type>.</span></span> <span data-ttu-id="fca71-116">Die Eingabe ist ein XAML-Typ.</span><span class="sxs-lookup"><span data-stu-id="fca71-116">The input is a XAML type.</span></span> <span data-ttu-id="fca71-117">Die Beziehung zwischen dem Eingabe-XAML-Typ und der Ausgabe-CLR <xref:System.Type> besteht darin, dass die Ausgabe <xref:System.Type> die <xref:System.Xaml.XamlType.UnderlyingType%2A> der Eingabe <xref:System.Xaml.XamlType>ist, nachdem der erforderliche <xref:System.Xaml.XamlType> XAML-Schemakontext und der Dienst, den <xref:System.Windows.Markup.IXamlTypeResolver> der Kontext bereitstellt, nachuntersucht wurde.</span><span class="sxs-lookup"><span data-stu-id="fca71-117">The relationship between the input XAML type and the output CLR <xref:System.Type> is that the output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input <xref:System.Xaml.XamlType>, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>

<span data-ttu-id="fca71-118">In .NET XAML Services wird die Verarbeitung für <xref:System.Windows.Markup.TypeExtension> diese Markuperweiterung durch die Klasse definiert.</span><span class="sxs-lookup"><span data-stu-id="fca71-118">In .NET XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.TypeExtension> class.</span></span>

<span data-ttu-id="fca71-119">In bestimmten Frameworkimplementierungen können <xref:System.Type> einige Eigenschaften, die als Wert annehmen, den Namen `Name`des Typs direkt akzeptieren (den Zeichenfolgenwert des Typs ).</span><span class="sxs-lookup"><span data-stu-id="fca71-119">In specific framework implementations, some properties that take <xref:System.Type> as a value can accept the name of the type directly (the string value of the type `Name`).</span></span> <span data-ttu-id="fca71-120">Die Implementierung dieses Verhaltens ist jedoch ein komplexes Szenario.</span><span class="sxs-lookup"><span data-stu-id="fca71-120">However, implementing this behavior is a complex scenario.</span></span> <span data-ttu-id="fca71-121">Beispiele finden Sie im folgenden Abschnitt "WPF-Verwendungshinweise".</span><span class="sxs-lookup"><span data-stu-id="fca71-121">For examples, see the "WPF Usage Notes" section that follows.</span></span>

<span data-ttu-id="fca71-122">Die Attributsyntax ist die mit dieser Markuperweiterung am häufigsten verwendete Syntax.</span><span class="sxs-lookup"><span data-stu-id="fca71-122">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="fca71-123">Das Zeichenfolgentoken, das auf die `x:Type`-Bezeichnerzeichenfolge folgt, wird als <xref:System.Windows.Markup.TypeExtension.TypeName%2A>-Wert der zugrunde liegenden <xref:System.Windows.Markup.TypeExtension>-Erweiterungsklasse zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="fca71-123">The string token provided after the `x:Type` identifier string is assigned as the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> value of the underlying <xref:System.Windows.Markup.TypeExtension> extension class.</span></span> <span data-ttu-id="fca71-124">Unter dem Standardmäßigen XAML-Schemakontext für .NET XAML Services, der auf CLR-Typen basiert, ist der Wert dieses Attributs entweder der <xref:System.Reflection.MemberInfo.Name%2A> des gewünschten Typs oder enthält das <xref:System.Reflection.MemberInfo.Name%2A> Präfix für eine nicht standardmäßige XAML-Namespacezuordnung.</span><span class="sxs-lookup"><span data-stu-id="fca71-124">Under the default XAML schema context for .NET XAML Services, which is based on CLR types, the value of this attribute is either the <xref:System.Reflection.MemberInfo.Name%2A> of the desired type, or contains that <xref:System.Reflection.MemberInfo.Name%2A> preceded by a prefix for a non-default XAML namespace mapping.</span></span>

<span data-ttu-id="fca71-125">Die `x:Type` Markuperweiterung kann in der Objektelementsyntax verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="fca71-125">The `x:Type` markup extension can be used in object element syntax.</span></span> <span data-ttu-id="fca71-126">In diesem Fall ist die <xref:System.Windows.Markup.TypeExtension.TypeName%2A> Angabe des Werts der Eigenschaft erforderlich, um die Erweiterung ordnungsgemäß zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="fca71-126">In this case, specifying the value of the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> property is required to properly initialize the extension.</span></span>

<span data-ttu-id="fca71-127">Die `x:Type` Markuperweiterung kann auch als ausführliches Attribut verwendet werden. Diese Verwendung ist jedoch nicht typisch:`<object property="{x:Type TypeName=typeNameValue}" .../>`</span><span class="sxs-lookup"><span data-stu-id="fca71-127">The `x:Type` markup extension can also be used as a verbose attribute; however this use is not typical: `<object property="{x:Type TypeName=typeNameValue}" .../>`</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="fca71-128">Hinweise zur WPF-Verwendung</span><span class="sxs-lookup"><span data-stu-id="fca71-128">WPF Usage Notes</span></span>

### <a name="default-xaml-namespace-and-type-mapping"></a><span data-ttu-id="fca71-129">Standard-XAML-Namespace und Typzuordnung</span><span class="sxs-lookup"><span data-stu-id="fca71-129">Default XAML Namespace and Type Mapping</span></span>

<span data-ttu-id="fca71-130">Der standardmäßige XAML-Namespace für die WPF-Programmierung enthält die meisten XAML-Typen, die Sie für typische XAML-Szenarien benötigen. Daher können Sie häufig Präfixe vermeiden, wenn Sie auf XAML-Typwerte verweisen.</span><span class="sxs-lookup"><span data-stu-id="fca71-130">The default XAML namespace for WPF programming contains most of the XAML types you need for typical XAML scenarios; therefore, you can often avoid prefixes when referencing XAML type values.</span></span> <span data-ttu-id="fca71-131">Möglicherweise müssen Sie ein Präfix zuordnen, wenn Sie auf einen Typ aus einer benutzerdefinierten Assembly oder auf Typen verweisen, die in einer WPF-Assembly vorhanden sind, aber aus einem CLR-Namespace stammen, der nicht dem standardmäßigen XAML-Namespace zugeordnet wurde.</span><span class="sxs-lookup"><span data-stu-id="fca71-131">You might need to map a prefix if you are referencing a type from a custom assembly or for types that exist in a WPF assembly but are from a CLR namespace that was not mapped to the default XAML namespace.</span></span> <span data-ttu-id="fca71-132">Weitere Informationen zu Präfixen, XAML-Namespaces und Zuordnung von CLR-Namespaces finden Sie unter [XAML-Namespaces und Namespace-Zuordnung für WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="fca71-132">For more information about prefixes, XAML namespaces, and mapping CLR namespaces, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>

### <a name="type-properties-that-support-typename-as-string"></a><span data-ttu-id="fca71-133">Typeigenschaften, die Typename-as-String unterstützen</span><span class="sxs-lookup"><span data-stu-id="fca71-133">Type Properties That Support Typename-as-String</span></span>

<span data-ttu-id="fca71-134">WPF unterstützt Techniken, die die Angabe des <xref:System.Type> Werts `x:Type` einiger Eigenschaften des Typs ermöglichen, ohne dass eine Markuperweiterungsverwendung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="fca71-134">WPF supports techniques that enable specifying the value of some properties of type <xref:System.Type> without requiring an `x:Type` markup extension usage.</span></span> <span data-ttu-id="fca71-135">Stattdessen können Sie den Wert als Zeichenfolge angeben, die den Typ benennt.</span><span class="sxs-lookup"><span data-stu-id="fca71-135">Instead, you can specify the value as a string that names the type.</span></span> <span data-ttu-id="fca71-136">Beispiele hierfür <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>sind und .</span><span class="sxs-lookup"><span data-stu-id="fca71-136">Examples of this are <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> and <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fca71-137">Unterstützung für dieses Verhalten wird weder durch Typkonverter noch über Markuperweiterungen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="fca71-137">Support for this behavior is not provided through either type converters or markup extensions.</span></span> <span data-ttu-id="fca71-138">Stattdessen handelt es sich um ein <xref:System.Windows.FrameworkElementFactory>Aufschubverhalten, das über implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="fca71-138">Instead, this is a deferral behavior implemented through <xref:System.Windows.FrameworkElementFactory>.</span></span>

<span data-ttu-id="fca71-139">Silverlight unterstützt eine ähnliche Konvention.</span><span class="sxs-lookup"><span data-stu-id="fca71-139">Silverlight supports a similar convention.</span></span> <span data-ttu-id="fca71-140">Tatsächlich unterstützt `{x:Type}` Silverlight derzeit keine XAML-Sprachunterstützung und akzeptiert `{x:Type}` keine Verwendungen außerhalb einiger Umstände, die die WPF-Silverlight XAML-Migration unterstützen sollen.</span><span class="sxs-lookup"><span data-stu-id="fca71-140">In fact, Silverlight does not currently support `{x:Type}` in its XAML language support, and does not accept `{x:Type}` usages outside of a few circumstances that are intended to support WPF-Silverlight XAML migration.</span></span> <span data-ttu-id="fca71-141">Daher ist das Typname-as-String-Verhalten in allen Silverlight-Eigenschaftenauswertungen integriert, bei denen a <xref:System.Type> der Wert ist.</span><span class="sxs-lookup"><span data-stu-id="fca71-141">Therefore, the typename-as-string behavior is built-in to all Silverlight native property evaluation where a <xref:System.Type> is the value.</span></span>

## <a name="xaml-2009"></a><span data-ttu-id="fca71-142">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="fca71-142">XAML 2009</span></span>

<span data-ttu-id="fca71-143">XAML 2009 bietet zusätzliche Unterstützung für generische Typen `x:TypeArguments` und `x:Type` ändert das Feature-Verhalten von und bietet diese Unterstützung.</span><span class="sxs-lookup"><span data-stu-id="fca71-143">XAML 2009 provides additional support for generic types and modifies the feature behavior of `x:TypeArguments` and `x:Type` to provide this support.</span></span>

- <span data-ttu-id="fca71-144">`x:TypeArguments`und das zugeordnete Objektelement für eine generische Objektinstanziierung kann sich auf anderen Elementen als dem Stamm befinden.</span><span class="sxs-lookup"><span data-stu-id="fca71-144">`x:TypeArguments` and the associated object element for a generic object instantiation can be on elements other than the root.</span></span> <span data-ttu-id="fca71-145">Weitere Informationen finden Sie im Abschnitt "XAML 2009" der [x:TypeArguments-Richtlinie](xtypearguments-directive.md).</span><span class="sxs-lookup"><span data-stu-id="fca71-145">For more information, see the "XAML 2009" section of [x:TypeArguments Directive](xtypearguments-directive.md).</span></span>

- <span data-ttu-id="fca71-146">XAML 2009 unterstützt eine Syntax zum Angeben der Einschränkung eines generischen Typs in Markup.</span><span class="sxs-lookup"><span data-stu-id="fca71-146">XAML 2009 supports a syntax for specifying a generic type's constraint in markup.</span></span> <span data-ttu-id="fca71-147">Dies kann `x:TypeArguments`von `x:Type`verwendet werden, von , oder von den beiden Features in Kombination.</span><span class="sxs-lookup"><span data-stu-id="fca71-147">This can be used by `x:TypeArguments`, by `x:Type`, or by the two features in combination.</span></span>

- <span data-ttu-id="fca71-148">Die WPF XAML-Implementierung bei der Verarbeitung von XAML 2009 für die Auslastung <xref:System.Type>fügt diese Funktion auch dem impliziten Typkonvertierungsverhalten für bestimmte Frameworkeigenschaften hinzu, die vom Typ verwenden.</span><span class="sxs-lookup"><span data-stu-id="fca71-148">WPF XAML implementation when processing XAML 2009 for load also adds this capability to the implicit type conversion behavior for certain framework properties that use type <xref:System.Type>.</span></span>

<span data-ttu-id="fca71-149">In WPF können Sie XAML 2009-Features verwenden, jedoch nur für loses XAML (XAML, das nicht markupkompiliert ist).</span><span class="sxs-lookup"><span data-stu-id="fca71-149">In WPF, you can use XAML 2009 features but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="fca71-150">Markupkompilierte XAML für WPF und die BAML-Form von XAML unterstützen die XAML 2009-Schlüsselwörter und -Funktionen derzeit nicht.</span><span class="sxs-lookup"><span data-stu-id="fca71-150">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>

## <a name="see-also"></a><span data-ttu-id="fca71-151">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fca71-151">See also</span></span>

- <xref:System.Windows.Style>
- [<span data-ttu-id="fca71-152">Erstellen von Formaten und Vorlagen</span><span class="sxs-lookup"><span data-stu-id="fca71-152">Styling and Templating</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="fca71-153">Übersicht über XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="fca71-153">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
- [<span data-ttu-id="fca71-154">Markuperweiterungen und WPF-XAML</span><span class="sxs-lookup"><span data-stu-id="fca71-154">Markup Extensions and WPF XAML</span></span>](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)