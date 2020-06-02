---
title: Enum-Entwurf
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
ms.openlocfilehash: efdfcda95a67941f0fde5f7a96467af7dd374396
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280139"
---
# <a name="enum-design"></a><span data-ttu-id="38b37-102">Enum-Entwurf</span><span class="sxs-lookup"><span data-stu-id="38b37-102">Enum Design</span></span>

<span data-ttu-id="38b37-103">Enumerationswerte sind eine besondere Art von Werttyp.</span><span class="sxs-lookup"><span data-stu-id="38b37-103">Enums are a special kind of value type.</span></span> <span data-ttu-id="38b37-104">Es gibt zwei Arten von Aufständen: einfache Aufteilungs-und flagumerationszeichen.</span><span class="sxs-lookup"><span data-stu-id="38b37-104">There are two kinds of enums: simple enums and flag enums.</span></span>

<span data-ttu-id="38b37-105">Einfache Aufstellungen stellen kleine geschlossene Sätze von Auswahlmöglichkeiten dar.</span><span class="sxs-lookup"><span data-stu-id="38b37-105">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="38b37-106">Ein gängiges Beispiel für die einfache-Enumeration ist ein Satz von Farben.</span><span class="sxs-lookup"><span data-stu-id="38b37-106">A common example of the simple enum is a set of colors.</span></span>

<span data-ttu-id="38b37-107">Flag-Enumerationen sind so konzipiert, dass bitweise Vorgänge für die Enumerationswerte unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="38b37-107">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="38b37-108">Ein gängiges Beispiel für die Flags-Enumeration ist eine Liste von Optionen.</span><span class="sxs-lookup"><span data-stu-id="38b37-108">A common example of the flags enum is a list of options.</span></span>

<span data-ttu-id="38b37-109">✔️ eine Enumeration verwenden, um Parameter, Eigenschaften und Rückgabewerte, die Sätze von Werten darstellen, stark einzugeben.</span><span class="sxs-lookup"><span data-stu-id="38b37-109">✔️ DO use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>

<span data-ttu-id="38b37-110">✔️ bevorzugen die Verwendung einer Enumeration anstelle von statischen Konstanten.</span><span class="sxs-lookup"><span data-stu-id="38b37-110">✔️ DO favor using an enum instead of static constants.</span></span>

<span data-ttu-id="38b37-111">❌Verwenden Sie keine Enumeration für geöffnete Sätze (z. b. die Betriebssystemversion, die Namen der Freunde usw.).</span><span class="sxs-lookup"><span data-stu-id="38b37-111">❌ DO NOT use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>

<span data-ttu-id="38b37-112">❌Geben Sie keine reservierten Enumerationswerte an, die für die zukünftige Verwendung vorgesehen sind.</span><span class="sxs-lookup"><span data-stu-id="38b37-112">❌ DO NOT provide reserved enum values that are intended for future use.</span></span>

<span data-ttu-id="38b37-113">Sie können der vorhandenen Enumeration jederzeit einfach Werte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="38b37-113">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="38b37-114">Weitere Informationen zum Hinzufügen von Werten zu enumeraten finden [Sie unter Hinzufügen von Werten zu](#add_value) Enumerationswerten</span><span class="sxs-lookup"><span data-stu-id="38b37-114">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="38b37-115">Reservierte Werte verschmutzen lediglich den Satz realer Werte und führen tendenziell zu Benutzerfehlern.</span><span class="sxs-lookup"><span data-stu-id="38b37-115">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>

<span data-ttu-id="38b37-116">❌Vermeiden Sie die öffentliche Offenlegung von Enumerationswerten mit nur einem Wert</span><span class="sxs-lookup"><span data-stu-id="38b37-116">❌ AVOID publicly exposing enums with only one value.</span></span>

<span data-ttu-id="38b37-117">Eine gängige Vorgehensweise, um die zukünftige Erweiterbarkeit von C-APIs sicherzustellen, besteht darin, den Methoden Signaturen reservierte Parameter hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="38b37-117">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="38b37-118">Solche reservierten Parameter können als Enumerationswerte mit einem einzelnen Standardwert ausgedrückt werden.</span><span class="sxs-lookup"><span data-stu-id="38b37-118">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="38b37-119">Dies sollte nicht in verwalteten APIs erfolgen.</span><span class="sxs-lookup"><span data-stu-id="38b37-119">This should not be done in managed APIs.</span></span> <span data-ttu-id="38b37-120">Die Methoden Überladung ermöglicht das Hinzufügen von Parametern in zukünftigen Versionen.</span><span class="sxs-lookup"><span data-stu-id="38b37-120">Method overloading allows adding parameters in future releases.</span></span>

<span data-ttu-id="38b37-121">❌Fügen Sie keine Sentinel-Werte in Enumerationswerte ein.</span><span class="sxs-lookup"><span data-stu-id="38b37-121">❌ DO NOT include sentinel values in enums.</span></span>

<span data-ttu-id="38b37-122">Obwohl Sie für Frameworkentwickler manchmal hilfreich sind, sind Sentinel-Werte für Benutzer des Frameworks verwirrend.</span><span class="sxs-lookup"><span data-stu-id="38b37-122">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="38b37-123">Sie werden verwendet, um den Zustand der Enumeration zu verfolgen, anstatt einen der Werte aus dem Satz zu verwenden, der durch die Enumeration repräsentiert wird.</span><span class="sxs-lookup"><span data-stu-id="38b37-123">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>

<span data-ttu-id="38b37-124">✔️ für einfache Enumerationswerte den Wert 0 (null) bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="38b37-124">✔️ DO provide a value of zero on simple enums.</span></span>

<span data-ttu-id="38b37-125">Es empfiehlt sich, den Wert in etwa "None" zu aufrufen.</span><span class="sxs-lookup"><span data-stu-id="38b37-125">Consider calling the value something like "None."</span></span> <span data-ttu-id="38b37-126">Wenn ein solcher Wert für diese bestimmte Enumeration nicht geeignet ist, sollte dem am häufigsten voreingestellten Standardwert für die Enumeration der zugrunde liegende Wert 0 (null) zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="38b37-126">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>

<span data-ttu-id="38b37-127">✔️ sollten Sie die Verwendung von <xref:System.Int32> (standardmäßig in den meisten Programmiersprachen) als zugrunde liegenden Typ einer-Aufzählung in Erwägung gezogen, es sei denn, eine der folgenden ist true</span><span class="sxs-lookup"><span data-stu-id="38b37-127">✔️ CONSIDER using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>

- <span data-ttu-id="38b37-128">Die Enumeration ist eine Flags-Enumeration, und Sie verfügen über mehr als 32 Flags oder erwarten, dass in der Zukunft mehr vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="38b37-128">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>

- <span data-ttu-id="38b37-129">Der zugrunde liegende Typ muss sich von der <xref:System.Int32> einfacheren Interoperabilität mit nicht verwaltetem Code unterscheiden, der andere enums erwartet.</span><span class="sxs-lookup"><span data-stu-id="38b37-129">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>

- <span data-ttu-id="38b37-130">Ein kleinerer zugrunde liegender Typ führt zu erheblichen Einsparungen im Bereich.</span><span class="sxs-lookup"><span data-stu-id="38b37-130">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="38b37-131">Wenn Sie davon ausgehen, dass die Aufzählung hauptsächlich als Argument für die Ablauf Steuerung verwendet werden soll, hat die Größe kaum einen Unterschied.</span><span class="sxs-lookup"><span data-stu-id="38b37-131">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="38b37-132">Die Größen Einsparungen können in folgenden Größen erheblich sein:</span><span class="sxs-lookup"><span data-stu-id="38b37-132">The size savings might be significant if:</span></span>

  - <span data-ttu-id="38b37-133">Sie erwarten, dass die Enumeration als Feld in einer sehr häufig instanziierten Struktur oder Klasse verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="38b37-133">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>

  - <span data-ttu-id="38b37-134">Sie erwarten, dass Benutzer große Arrays oder Auflistungen der Enumeration-Instanzen erstellen.</span><span class="sxs-lookup"><span data-stu-id="38b37-134">You expect users to create large arrays or collections of the enum instances.</span></span>

  - <span data-ttu-id="38b37-135">Sie erwarten, dass eine große Anzahl von Instanzen der Enumeration serialisiert wird.</span><span class="sxs-lookup"><span data-stu-id="38b37-135">You expect a large number of instances of the enum to be serialized.</span></span>

<span data-ttu-id="38b37-136">Beachten Sie bei der in-Memory-Verwendung, dass verwaltete Objekte immer `DWORD` ausgerichtet sind, sodass Sie in einer Instanz tatsächlich mehrere Enumerationen oder andere kleine Strukturen benötigen, um einen Unterschied zu erstellen, da die gesamte instanzgröße immer auf einen aufgerundet wird `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="38b37-136">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>

<span data-ttu-id="38b37-137">✔️ durch eine namensflag-Enumerationen mit Plural-Nomen oder nominalen Ausdrücken und einfachen Enumerationen mit Singular-Nomen oder Substantiv Ausdrücken.</span><span class="sxs-lookup"><span data-stu-id="38b37-137">✔️ DO name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>

<span data-ttu-id="38b37-138">❌Nicht direkt erweitern <xref:System.Enum?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="38b37-138">❌ DO NOT extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>

<span data-ttu-id="38b37-139"><xref:System.Enum?displayProperty=nameWithType>ist ein spezieller Typ, der von der CLR verwendet wird, um benutzerdefinierte Enumerationen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="38b37-139"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="38b37-140">Die meisten Programmiersprachen bieten ein Programmier Element, das Ihnen den Zugriff auf diese Funktionalität ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="38b37-140">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="38b37-141">Beispielsweise wird in c# das- `enum` Schlüsselwort verwendet, um eine Enumeration zu definieren.</span><span class="sxs-lookup"><span data-stu-id="38b37-141">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>

<a name="design"></a>

### <a name="designing-flag-enums"></a><span data-ttu-id="38b37-142">Entwerfen von Flag-Aufständen</span><span class="sxs-lookup"><span data-stu-id="38b37-142">Designing Flag Enums</span></span>

<span data-ttu-id="38b37-143">✔️ anwenden, um auf-auf-auf-auf-auf- <xref:System.FlagsAttribute?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="38b37-143">✔️ DO apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="38b37-144">Wenden Sie dieses Attribut nicht auf einfache auffüge Aufgaben an.</span><span class="sxs-lookup"><span data-stu-id="38b37-144">Do not apply this attribute to simple enums.</span></span>

<span data-ttu-id="38b37-145">✔️ für die Flag-Enumerationswerte zwei Möglichkeiten verwenden, damit Sie mit der bitweisen OR-Operation frei kombiniert werden können.</span><span class="sxs-lookup"><span data-stu-id="38b37-145">✔️ DO use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>

<span data-ttu-id="38b37-146">✔️ sollten besondere Enumerationswerte für häufig verwendete Kombinationen von Flags bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="38b37-146">✔️ CONSIDER providing special enum values for commonly used combinations of flags.</span></span>

<span data-ttu-id="38b37-147">Bitweise Vorgänge sind ein erweitertes Konzept, das für einfache Aufgaben nicht erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="38b37-147">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="38b37-148"><xref:System.IO.FileAccess.ReadWrite>ein Beispiel für einen solchen besonderen Wert.</span><span class="sxs-lookup"><span data-stu-id="38b37-148"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>

<span data-ttu-id="38b37-149">❌Vermeiden Sie das Erstellen von Flag-enumeraten, wenn bestimmte Kombinationen von Werten ungültig sind</span><span class="sxs-lookup"><span data-stu-id="38b37-149">❌ AVOID creating flag enums where certain combinations of values are invalid.</span></span>

<span data-ttu-id="38b37-150">❌Vermeiden Sie die Verwendung von Flag-Enumerationswerten von 0 (null), es sei denn, der Wert steht für "alle Flags sind gelöscht" und entsprechend der Bezeichnung durch die nächste Richtlinie</span><span class="sxs-lookup"><span data-stu-id="38b37-150">❌ AVOID using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>

<span data-ttu-id="38b37-151">✔️ den Wert 0 (null) der Flag-Enumerationsnamen `None` .</span><span class="sxs-lookup"><span data-stu-id="38b37-151">✔️ DO name the zero value of flag enums `None`.</span></span> <span data-ttu-id="38b37-152">Bei einer Flag-Enumeration muss der Wert immer lauten, dass alle Flags gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="38b37-152">For a flag enum, the value must always mean "all flags are cleared."</span></span>

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a><span data-ttu-id="38b37-153">Hinzufügen von Wert zu enumeraten</span><span class="sxs-lookup"><span data-stu-id="38b37-153">Adding Value to Enums</span></span>

<span data-ttu-id="38b37-154">Es kommt häufig vor, dass Sie einer Enumeration Werte hinzufügen müssen, nachdem Sie Sie bereits geliefert haben.</span><span class="sxs-lookup"><span data-stu-id="38b37-154">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="38b37-155">Es gibt ein potenzielles Problem mit der Anwendungs Kompatibilität, wenn der neu hinzugefügte Wert von einer vorhandenen API zurückgegeben wird, da schlecht geschriebene Anwendungen den neuen Wert möglicherweise nicht ordnungsgemäß verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="38b37-155">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>

<span data-ttu-id="38b37-156">✔️ ggf. Werte zu Enumerationswerten hinzufügen, trotz eines geringen Kompatibilitäts Risikos.</span><span class="sxs-lookup"><span data-stu-id="38b37-156">✔️ CONSIDER adding values to enums, despite a small compatibility risk.</span></span>

<span data-ttu-id="38b37-157">Wenn Sie über echte Daten über Anwendungs Inkompatibilitäten verfügen, die durch Ergänzungen zu einer Enumeration verursacht werden, sollten Sie eine neue API hinzufügen, die die neuen und alten Werte zurückgibt, und die alte API als veraltet kennzeichnen, sodass nur die alten Werte zurückgegeben werden sollten.</span><span class="sxs-lookup"><span data-stu-id="38b37-157">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="38b37-158">Dadurch wird sichergestellt, dass Ihre vorhandenen Anwendungen kompatibel bleiben.</span><span class="sxs-lookup"><span data-stu-id="38b37-158">This will ensure that your existing applications remain compatible.</span></span>

<span data-ttu-id="38b37-159">*Teile © 2005, 2009 Microsoft Corporation. Alle Rechte vorbehalten.*</span><span class="sxs-lookup"><span data-stu-id="38b37-159">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="38b37-160">*Nachdruck mit Genehmigung von Pearson Education, Inc aus [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) von Krzysztof Cwalina und Brad Abrams, veröffentlicht am 22. Oktober 2008 durch Addison-Wesley Professional als Teil der Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="38b37-160">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="38b37-161">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="38b37-161">See also</span></span>

- [<span data-ttu-id="38b37-162">Typentwurfs Richtlinien</span><span class="sxs-lookup"><span data-stu-id="38b37-162">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="38b37-163">Framework-Entwurfs Richtlinien</span><span class="sxs-lookup"><span data-stu-id="38b37-163">Framework Design Guidelines</span></span>](index.md)
