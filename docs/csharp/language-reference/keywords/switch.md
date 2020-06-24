---
title: switch-Anweisung in C#
ms.date: 04/09/2019
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
ms.openlocfilehash: 9335399be2d4909a02fecbf2959c6f5608664732
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493668"
---
# <a name="switch-c-reference"></a><span data-ttu-id="4b4e2-102">switch (C#-Referenz)</span><span class="sxs-lookup"><span data-stu-id="4b4e2-102">switch (C# reference)</span></span>

<span data-ttu-id="4b4e2-103">In diesem Artikel wird die `switch`-Anweisung vorgestellt.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-103">This article covers the `switch` statement.</span></span> <span data-ttu-id="4b4e2-104">Informationen zum `switch`-Ausdruck (eingeführt in C# 8.0) finden Sie im Artikel zu [`switch`-Ausdrücken](../operators/switch-expression.md) im Abschnitt [Ausdrücke und Operatoren](../operators/index.md).</span><span class="sxs-lookup"><span data-stu-id="4b4e2-104">For information on the `switch` expression (introduced in C# 8.0), see the article on [`switch` expressions](../operators/switch-expression.md) in the [expressions and operators](../operators/index.md) section.</span></span>

<span data-ttu-id="4b4e2-105">`switch` ist eine Auswahlanweisung, die einen einzelnen *switch-Abschnitt* zum Ausführen aus einer Liste von Kandidaten auswählt, die auf einem Mustertreffer mit dem *Vergleichsausdruck* basiert.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-105">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="4b4e2-106">Die Anweisung `switch` wird häufig als Alternative zu einem [if-else](if-else.md)-Konstrukt verwendet, wenn ein einzelner Ausdruck mit drei oder mehr Bedingungen getestet wird.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-106">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="4b4e2-107">Die folgende Anweisung `switch` bestimmt z.B., ob eine Variable des Typs `Color` einen von drei Werten hat:</span><span class="sxs-lookup"><span data-stu-id="4b4e2-107">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="4b4e2-108">Dies entspricht dem folgenden Beispiel, das ein `if`-`else`-Konstrukt verwendet.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-108">It's equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="4b4e2-109">Der Vergleichsausdruck</span><span class="sxs-lookup"><span data-stu-id="4b4e2-109">The match expression</span></span>

<span data-ttu-id="4b4e2-110">Der Vergleichsausdruck stellt den Wert bereit, mit dem die Muster in den Bezeichnungen `case` verglichen werden.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-110">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="4b4e2-111">Die Syntax lautet:</span><span class="sxs-lookup"><span data-stu-id="4b4e2-111">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="4b4e2-112">In C# 6 und früher muss der Vergleichsausdruck ein Ausdruck sein, der einen Wert der folgenden Typen zurückgibt:</span><span class="sxs-lookup"><span data-stu-id="4b4e2-112">In C# 6 and earlier, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="4b4e2-113">Ein [char](../builtin-types/char.md)</span><span class="sxs-lookup"><span data-stu-id="4b4e2-113">a [char](../builtin-types/char.md).</span></span>
- <span data-ttu-id="4b4e2-114">Eine [Zeichenfolge](../builtin-types/reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="4b4e2-114">a [string](../builtin-types/reference-types.md).</span></span>
- <span data-ttu-id="4b4e2-115">Ein [bool](../builtin-types/bool.md)</span><span class="sxs-lookup"><span data-stu-id="4b4e2-115">a [bool](../builtin-types/bool.md).</span></span>
- <span data-ttu-id="4b4e2-116">Ein [ganzzahliger](../builtin-types/integral-numeric-types.md) Wert wie `int` oder `long`.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-116">an [integral](../builtin-types/integral-numeric-types.md) value, such as an `int` or a `long`.</span></span>
- <span data-ttu-id="4b4e2-117">Ein [Enumerations](../builtin-types/enum.md)wert</span><span class="sxs-lookup"><span data-stu-id="4b4e2-117">an [enum](../builtin-types/enum.md) value.</span></span>

<span data-ttu-id="4b4e2-118">Ab C# 7.0 kann der Vergleichsausdruck jeder Ausdruck sein, der nicht NULL ist.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-118">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="4b4e2-119">Der switch-Abschnitt</span><span class="sxs-lookup"><span data-stu-id="4b4e2-119">The switch section</span></span>

<span data-ttu-id="4b4e2-120">Eine `switch`-Anweisung enthält eine oder mehrere switch-Abschnitte.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-120">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="4b4e2-121">Jeder switch-Abschnitt enthält mindestens eine *case-Bezeichnung* (eine case- oder Standardbezeichnung) gefolgt von mindestens einer Anweisung.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-121">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="4b4e2-122">Die `switch`-Anweisung kann höchstens eine Standardbezeichnung in einem beliebigen switch-Abschnitt enthalten.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-122">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="4b4e2-123">Das folgende Beispiel zeigt eine einfache `switch`-Anweisung, die über drei switch-Abschnitte mit je zwei Anweisungen verfügt.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-123">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="4b4e2-124">Der zweite switch-Abschnitt enthält die Bezeichnungen `case 2:` und `case 3:`.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-124">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="4b4e2-125">Eine `switch`-Anweisung kann eine beliebige Anzahl von switch-Abschnitten enthalten, und jeder Abschnitt kann eine oder mehrere case-Bezeichnungen haben, wie im folgend Beispiel gezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-125">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="4b4e2-126">Allerdings können zwei case-Bezeichnungen nicht denselben Ausdruck enthalten.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-126">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="4b4e2-127">Nur ein switch-Abschnitt einer switch-Anweisung wir ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-127">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="4b4e2-128">C# lässt nicht zu, dass die Ausführung von einem switch-Abschnitt zum nächsten fortgesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-128">C# doesn't allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="4b4e2-129">Deshalb verursacht der folgende Code den Compilerfehler CS0163: „Das Steuerelement kann nicht von einer case-Bezeichnung (\<case label>) zur nächsten fortfahren.“</span><span class="sxs-lookup"><span data-stu-id="4b4e2-129">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (\<case label>) to another."</span></span>

```csharp
switch (caseSwitch)
{
    // The following switch section causes an error.
    case 1:
        Console.WriteLine("Case 1...");
        // Add a break or other jump statement here.
    case 2:
        Console.WriteLine("... and/or Case 2");
        break;
}
```

<span data-ttu-id="4b4e2-130">Diese Anforderung wird normalerweise erfüllt, indem der switch-Abschnitt ausdrücklich durch Verwenden einer Anweisung [break](break.md), [goto](goto.md) oder [return](return.md) beendet wird.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-130">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="4b4e2-131">Der folgende Code ist jedoch auch gültig, da er sicherstellt, dass die Programmsteuerung nicht im switch-Abschnitt `default` fortfährt.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-131">However, the following code is also valid, because it ensures that program control can't fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="4b4e2-132">Die Ausführung der Anweisungsliste im switch-Abschnitt mit einer case-Bezeichnung, die den Vergleichsausdruck vergleicht, beginnt mit der ersten Anweisung und durchläuft in der Regel die Anweisungsliste, bis eine jump-Anweisung erreicht wird, z.B. `break`, `goto case`, `goto label`, `return` oder `throw`.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-132">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="4b4e2-133">An diesem Punkt wird die Steuerung der `switch`-Anweisung entzogen oder an eine andere case-Bezeichnung übertragen.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-133">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="4b4e2-134">Wenn eine `goto`-Anweisung verwendet wird, muss sie die Steuerung an eine konstante Bezeichnung übergeben.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-134">A `goto` statement, if it's used, must transfer control to a constant label.</span></span> <span data-ttu-id="4b4e2-135">Diese Einschränkung ist notwendig, da der Versuch, die Steuerung an eine nicht konstante Bezeichnung zu übergeben, unerwünschte Nebeneffekte haben kann, z.B. kann die Steuerung an eine nicht beabsichtigte Position im Code übergeben werden, oder es kann eine Endlosschleife entstehen.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-135">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="4b4e2-136">case-Bezeichnungen</span><span class="sxs-lookup"><span data-stu-id="4b4e2-136">Case labels</span></span>

<span data-ttu-id="4b4e2-137">Jede case-Bezeichnung gibt ein Muster an, mit dem der Vergleichsausdruck verglichen werden soll (die Variable `caseSwitch` in den vorherigen Beispielen).</span><span class="sxs-lookup"><span data-stu-id="4b4e2-137">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="4b4e2-138">Wenn sie übereinstimmen, wird das Steuerelement an den switch-Abschnitt übertragen, der die **erste** übereinstimmende case-Bezeichnung enthält.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-138">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="4b4e2-139">Wenn keine case-Bezeichnung mit dem Vergleichsausdruck übereinstimmt, wird das Steuerelement an den Abschnitt mit der `default`-case-Bezeichnung übertragen, sofern vorhanden.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-139">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there's one.</span></span> <span data-ttu-id="4b4e2-140">Wenn kein `default`-case vorhanden ist, werden keine Anweisungen in jeglichen switch-Abschnitten ausgeführt, und ein Steuerelement wird außerhalb der `switch`-Anweisung übertragen.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-140">If there's no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="4b4e2-141">Informationen zur `switch`-Anweisung und zum Musterabgleich finden Sie im Abschnitt [Musterabgleich mit der `switch`-Anweisung](#pattern-matching with-the-switch-statement).</span><span class="sxs-lookup"><span data-stu-id="4b4e2-141">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern-matching with-the-switch-statement) section.</span></span>

<span data-ttu-id="4b4e2-142">Da C# 6 nur das Konstantenmuster unterstützt und die Wiederholung von Konstantenwerten nicht erlaubt, definieren case-Bezeichnungen exklusive Werte, und nur ein Muster kann mit dem Vergleichsausdruck übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-142">Because C# 6 supports only the constant pattern and doesn't allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="4b4e2-143">Daher ist die Reihenfolge, in der die `case`-Anweisungen auftauchen, unwichtig.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-143">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="4b4e2-144">Da in C# 7.0 jedoch andere Muster unterstützt werden, müssen case-Bezeichnungen keine gegenseitig ausschließenden Werte definieren, und mehrere Muster können mit dem Vergleichsausdruck übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-144">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="4b4e2-145">Da nur die Anweisungen im ersten switch-Abschnitt ausgeführt werden, die das übereinstimmende Muster enthalten, ist die Reihenfolge, in der `case`-Anweisungen erscheinen, nun wichtig.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-145">Because only the statements in the first switch section that contains the matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="4b4e2-146">Wenn C# einen switch-Abschnitt erkennt, dessen case-Anweisung oder Anweisungen eine Teilmenge der vorherigen Anweisungen ist oder einer entsprechen, erzeugt der Abschnitt den Compilerfehler CS8120: „Der Parameter wurde bereits von einem vorherigen Parameter verarbeitet.“</span><span class="sxs-lookup"><span data-stu-id="4b4e2-146">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="4b4e2-147">Das folgende Beispiel veranschaulicht eine `switch`-Anweisung, die eine Reihe von sich nicht gegenseitig ausschließenden Mustern verwendet.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-147">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="4b4e2-148">Wenn Sie den switch-Abschnitt `case 0:` verschieben, sodass er nicht länger der erste Abschnitt in der `switch`-Anweisung ist, erzeugt C# einen Compilerfehler, da eine Ganzzahl, deren Wert 0 ist, eine Teilmenge aller Ganzzahlen ist, die dem von der `case int val`-Anweisung definierten Muster entspricht.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-148">If you move the `case 0:` switch section so that it's no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="4b4e2-149">Sie können dieses Problem beheben und die Compilerwarnung auf eine von zwei Arten entfernen:</span><span class="sxs-lookup"><span data-stu-id="4b4e2-149">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="4b4e2-150">Durch das Ändern der Reihenfolge der switch-Abschnitte</span><span class="sxs-lookup"><span data-stu-id="4b4e2-150">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="4b4e2-151">Durch Verwenden einer [when-Klausel](#the-case-statement-and-the-when-clause) in der `case`-Bezeichnung</span><span class="sxs-lookup"><span data-stu-id="4b4e2-151">By using a [when clause](#the-case-statement-and-the-when-clause) in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="4b4e2-152">Der `default`-Case</span><span class="sxs-lookup"><span data-stu-id="4b4e2-152">The `default` case</span></span>

<span data-ttu-id="4b4e2-153">Der `default`-Case gibt den auszuführenden switch-Abschnitt an, wenn der Vergleichsausdruck nicht mit einer anderen `case`-Bezeichnung übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-153">The `default` case specifies the switch section to execute if the match expression doesn't match any other `case` label.</span></span> <span data-ttu-id="4b4e2-154">Wenn ein `default`-Case nicht vorhanden ist, und der Vergleichsausdruck nicht einer anderen `case`-Bezeichnung entspricht, fährt der Programmablauf mit der `switch`-Anweisung fort.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-154">If a `default` case is not present and the match expression doesn't match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="4b4e2-155">Der `default`-Case kann in beliebiger Reihenfolge in der `switch`-Anweisung auftauchen.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-155">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="4b4e2-156">Unabhängig von der Reihenfolge im Quellcode wird er immer zuletzt ausgewertet, nachdem alle `case`-Bezeichnungen ausgewertet wurden.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-156">Regardless of its order in the source code, it's always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="pattern-matching-with-the-switch-statement"></a><span data-ttu-id="4b4e2-157">Musterabgleich mit der `switch`-Anweisung</span><span class="sxs-lookup"><span data-stu-id="4b4e2-157">Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="4b4e2-158">Jede `case`-Anweisung definiert ein Muster, das, wenn es mit dem Vergleichsausdruck übereinstimmt, dafür sorgt, dass seine enthaltenden switch-Abschnitte ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-158">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="4b4e2-159">Alle Versionen von C# unterstützen Konstantenmuster.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-159">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="4b4e2-160">Die übrigen Muster werden ab C# 7.0 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-160">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="4b4e2-161">Konstantenmuster</span><span class="sxs-lookup"><span data-stu-id="4b4e2-161">Constant pattern</span></span>

<span data-ttu-id="4b4e2-162">Das Konstantenmuster testet, ob der Vergleichsausdruck einer festgelegten Konstanten entspricht.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-162">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="4b4e2-163">Die Syntax lautet:</span><span class="sxs-lookup"><span data-stu-id="4b4e2-163">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="4b4e2-164">wobei *constant* der zu testende Wert ist.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-164">where *constant* is the value to test for.</span></span> <span data-ttu-id="4b4e2-165">*constant* kann eine der folgenden konstanten Ausdrücke sein:</span><span class="sxs-lookup"><span data-stu-id="4b4e2-165">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="4b4e2-166">Ein [bool](../builtin-types/bool.md)-Literal: entweder `true` oder `false`</span><span class="sxs-lookup"><span data-stu-id="4b4e2-166">A [bool](../builtin-types/bool.md) literal: either `true` or `false`.</span></span>
- <span data-ttu-id="4b4e2-167">Eine [ganzzahlige](../builtin-types/integral-numeric-types.md) Konstante wie `int`, `long` oder `byte`.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-167">Any [integral](../builtin-types/integral-numeric-types.md) constant, such as an `int`, a `long`, or a `byte`.</span></span>
- <span data-ttu-id="4b4e2-168">Der Name einer deklarierten `const`-Variablen</span><span class="sxs-lookup"><span data-stu-id="4b4e2-168">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="4b4e2-169">Eine Enumerationskonstante.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-169">An enumeration constant.</span></span>
- <span data-ttu-id="4b4e2-170">Ein [char](../builtin-types/char.md)-Literal</span><span class="sxs-lookup"><span data-stu-id="4b4e2-170">A [char](../builtin-types/char.md) literal.</span></span>
- <span data-ttu-id="4b4e2-171">Ein [Zeichenfolgenliteral](../builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="4b4e2-171">A [string](../builtin-types/reference-types.md) literal.</span></span>

<span data-ttu-id="4b4e2-172">Der Konstantenausdruck wird wie folgt ausgewertet:</span><span class="sxs-lookup"><span data-stu-id="4b4e2-172">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="4b4e2-173">Wenn *expr* und *constant* integrale Typen sind, bestimmt der C#-Gleichheitsoperator, ob der Ausdruck `true` (d.h., ob `expr == constant`) zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-173">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="4b4e2-174">Andernfalls wird der Wert des Ausdrucks durch einen Aufruf der statischen Methode [Object.Equals (expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) bestimmt.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-174">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="4b4e2-175">Das folgende Beispiel verwendet das Konstantenmuster, um zu bestimmen, ob ein bestimmtes Datum ein Wochenende, der erste Tag der Arbeitswoche, der letzte Tag der Arbeitswoche oder die Mitte der Arbeitswoche ist.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-175">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="4b4e2-176">Es bewertet die Eigenschaft <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> des heutigen Tags mit den Membern der <xref:System.DayOfWeek>-Enumeration.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-176">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="4b4e2-177">Im folgenden Beispiel wird das Konstantenmuster verwendet, um Benutzereingaben in einer Konsolenanwendung zu steuern, die eine automatische Kaffeemaschine simuliert.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-177">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="4b4e2-178">Typmuster</span><span class="sxs-lookup"><span data-stu-id="4b4e2-178">Type pattern</span></span>

<span data-ttu-id="4b4e2-179">Das Typmuster ermöglicht die präzise Auswertung und Konvertierung des Typs.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-179">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="4b4e2-180">Wenn es mit der `switch`-Anweisung verwendet wird, um einen Musterabgleich auszuführen, wird getestet, ob eine Anweisung in einen bestimmten Typ konvertiert werden kann, und sofern dies möglich ist, wird es in eine Variable des Typs umgewandelt.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-180">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="4b4e2-181">Die Syntax lautet:</span><span class="sxs-lookup"><span data-stu-id="4b4e2-181">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="4b4e2-182">bei der *Typ* der Name des Typs ist, in den das Ergebnis von *expr* konvertiert wird, und *varname* das Objekt ist, in das das Ergebnis von *expr* konvertiert wird, wenn der Abgleich erfolgreich ist</span><span class="sxs-lookup"><span data-stu-id="4b4e2-182">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> <span data-ttu-id="4b4e2-183">Der Kompilierzeittyp von *expr* kann ab C# 7.1 ein generischen Parameter sein.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-183">The compile-time type of *expr* may be a generic type parameter, starting with C# 7.1.</span></span>

<span data-ttu-id="4b4e2-184">Der `case`-Ausdruck ist `true`, wenn eine der folgenden Aussagen zutrifft:</span><span class="sxs-lookup"><span data-stu-id="4b4e2-184">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="4b4e2-185">*expr* ist eine Instanz des gleichen Typs wie *Typ*.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-185">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="4b4e2-186">*expr* ist eine Instanz eines Typs, der von *Typ* abgeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-186">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="4b4e2-187">Das Ergebnis von *expr* kann, in anderen Worten, in eine Instanz von *Typ* umgewandelt werden.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-187">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="4b4e2-188">*expr* hat einen Kompilierzeittyp, der eine Basisklasse von *type* ist, und *expr* hat einen Laufzeittyp,der *type* ist oder von *type* abgeleitet wurde.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-188">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="4b4e2-189">Der *Kompilierzeittyp* einer Variablen ist der Typ der Variablen, wie es in der Deklaration des Typs definiert wurde.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-189">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="4b4e2-190">Der *Laufzeittyp* einer Variablen ist der Typ der Instanz, die dieser Variable zugewiesen wird.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-190">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="4b4e2-191">*expr* ist eine Instanz eines Typs, der die Schnittstelle *Typ* implementiert.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-191">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="4b4e2-192">Wenn der case-Ausdruck TRUE ist, ist *varname* definitiv zugewiesen und hat nur innerhalb des switch-Abschnitts einen lokalen Geltungsbereich.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-192">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="4b4e2-193">Beachten Sie, dass `null` nicht mit einem Typ übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-193">Note that `null` doesn't match a type.</span></span> <span data-ttu-id="4b4e2-194">Verwenden Sie folgende `case`-Bezeichnung, um `null` abzugleichen:</span><span class="sxs-lookup"><span data-stu-id="4b4e2-194">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="4b4e2-195">Im folgenden Beispiel wird mithilfe des Typmusters Informationen über die verschiedenen Arten von Auflistungstypen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-195">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="4b4e2-196">Anstelle von `object` könnten Sie eine generische Methode erstellen, indem Sie den Typ der Sammlung als Typparameter verwenden, wie im folgenden Code gezeigt:</span><span class="sxs-lookup"><span data-stu-id="4b4e2-196">Instead of `object`, you could make a generic method, using the type of the collection as the type parameter, as shown in the following code:</span></span>

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

<span data-ttu-id="4b4e2-197">Die generische Version unterscheidet sich auf zwei Arten vom ersten Beispiel.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-197">The generic version is different than the first sample in two ways.</span></span> <span data-ttu-id="4b4e2-198">Zunächst können Sie den `null`-Case verwenden.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-198">First, you can't use the `null` case.</span></span> <span data-ttu-id="4b4e2-199">Sie können keinen konstanten Case verwenden, da der Compiler nicht jeden beliebigen Typ `T` in einen anderen Typ als `object` konvertieren kann.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-199">You can't use any constant case because the compiler can't convert any arbitrary type `T` to any type other than `object`.</span></span> <span data-ttu-id="4b4e2-200">Was ein `default`-Case war, ist jetzt ein `object` ungleich NULL.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-200">What had been the `default` case now tests for a non-null `object`.</span></span> <span data-ttu-id="4b4e2-201">Das bedeutet, dass der `default`-Case nur `null` ergibt.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-201">That means the `default` case tests only for `null`.</span></span>

<span data-ttu-id="4b4e2-202">Ohne Musterabgleich könnte dieser Code wie folgt geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-202">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="4b4e2-203">Die Verwendung des Typmusterabgleichs erzeugt einen kompakteren, lesbaren Code, indem nicht mehr getestet werden muss, ob das Ergebnis einer Umwandlung `null` ist, oder um wiederholte Umwandlungen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-203">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a><span data-ttu-id="4b4e2-204">Die `case`-Anweisung und die `when`-Klausel</span><span class="sxs-lookup"><span data-stu-id="4b4e2-204">The `case` statement and the `when` clause</span></span>

<span data-ttu-id="4b4e2-205">Da sich case-Anweisungen ab C# 7.0 nicht gegenseitig ausschließen müssen, können Sie eine `when`-Klausel hinzufügen, um eine zusätzliche Bedingung anzugeben, die erfüllt werden muss, damit die case-Anweisung als TRUE ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-205">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="4b4e2-206">Die `when`-Klausel kann ein beliebiger Ausdruck sein, der einen booleschen Wert zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-206">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="4b4e2-207">Im folgenden Beispiel wird eine `Shape`-Basisklasse, eine `Rectangle`-Klasse, die von `Shape` abgeleitet wird, und eine `Square`-Klasse, die von `Rectangle` abgeleitet wird, definiert.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-207">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="4b4e2-208">Die `when`-Klausel wird verwendet, um sicherzustellen, dass `ShowShapeInfo` ein `Rectangle`-Objekt, dem eine gleiche Länge und Breite zugewiesen wurde, wie ein `Square` behandelt, selbst wenn es nicht als ein `Square`-Objekt instanziiert wurde.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-208">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it hasn't been instantiated as a `Square` object.</span></span> <span data-ttu-id="4b4e2-209">Diese Methode versucht weder Informationen über ein Objekt anzuzeigen, das `null` ist, noch über eine Form, deren Bereich NULL ist.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-209">The method doesn't attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="4b4e2-210">Beachten Sie, dass in diesem Beispiel die `when`-Klausel, die zu prüfen versucht, ob ein `Shape`-Objekt `null` ist, nicht ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-210">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` doesn't execute.</span></span> <span data-ttu-id="4b4e2-211">Das richtige Typmuster, um auf `null` zu testen, ist `case null:`.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-211">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4b4e2-212">C#-Sprachspezifikation</span><span class="sxs-lookup"><span data-stu-id="4b4e2-212">C# language specification</span></span>

<span data-ttu-id="4b4e2-213">Weitere Informationen finden Sie unter [Die switch-Anweisung](~/_csharplang/spec/statements.md#the-switch-statement) in der [C#-Sprachspezifikation](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="4b4e2-213">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="4b4e2-214">Die Sprachspezifikation ist die verbindliche Quelle für die Syntax und Verwendung von C#.</span><span class="sxs-lookup"><span data-stu-id="4b4e2-214">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b4e2-215">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4b4e2-215">See also</span></span>

- [<span data-ttu-id="4b4e2-216">C#-Referenz</span><span class="sxs-lookup"><span data-stu-id="4b4e2-216">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4b4e2-217">C#-Programmierhandbuch</span><span class="sxs-lookup"><span data-stu-id="4b4e2-217">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4b4e2-218">C#-Schlüsselwörter</span><span class="sxs-lookup"><span data-stu-id="4b4e2-218">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="4b4e2-219">if-else</span><span class="sxs-lookup"><span data-stu-id="4b4e2-219">if-else</span></span>](if-else.md)
- [<span data-ttu-id="4b4e2-220">Mustervergleich</span><span class="sxs-lookup"><span data-stu-id="4b4e2-220">Pattern Matching</span></span>](../../pattern-matching.md)
