---
title: Operator Mod
ms.date: 04/24/2018
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
ms.openlocfilehash: 32065567799b023556a018ae2f5ba338796e0b49
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401510"
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="f2b43-102">Mod-Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2b43-102">Mod operator (Visual Basic)</span></span>

<span data-ttu-id="f2b43-103">Dividiert zwei Zahlen und gibt nur den Rest zurück.</span><span class="sxs-lookup"><span data-stu-id="f2b43-103">Divides two numbers and returns only the remainder.</span></span>

## <a name="syntax"></a><span data-ttu-id="f2b43-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f2b43-104">Syntax</span></span>

```vb
result = number1 Mod number2
```

## <a name="parts"></a><span data-ttu-id="f2b43-105">Bestandteile</span><span class="sxs-lookup"><span data-stu-id="f2b43-105">Parts</span></span>

`result` \
<span data-ttu-id="f2b43-106">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f2b43-106">Required.</span></span> <span data-ttu-id="f2b43-107">Eine beliebige numerische Variable oder Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="f2b43-107">Any numeric variable or property.</span></span>

`number1` \
<span data-ttu-id="f2b43-108">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f2b43-108">Required.</span></span> <span data-ttu-id="f2b43-109">Ein beliebiger numerischer Ausdruck.</span><span class="sxs-lookup"><span data-stu-id="f2b43-109">Any numeric expression.</span></span>

`number2` \
<span data-ttu-id="f2b43-110">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f2b43-110">Required.</span></span> <span data-ttu-id="f2b43-111">Ein beliebiger numerischer Ausdruck.</span><span class="sxs-lookup"><span data-stu-id="f2b43-111">Any numeric expression.</span></span>

## <a name="supported-types"></a><span data-ttu-id="f2b43-112">Unterstützte Typen</span><span class="sxs-lookup"><span data-stu-id="f2b43-112">Supported types</span></span>

<span data-ttu-id="f2b43-113">allen numerischen Typen</span><span class="sxs-lookup"><span data-stu-id="f2b43-113">All numeric types.</span></span> <span data-ttu-id="f2b43-114">Dies schließt die unsignierten-und Gleit Komma Typen und ein `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="f2b43-114">This includes the unsigned and floating-point types and `Decimal`.</span></span>

## <a name="result"></a><span data-ttu-id="f2b43-115">Ergebnis</span><span class="sxs-lookup"><span data-stu-id="f2b43-115">Result</span></span>

<span data-ttu-id="f2b43-116">Das Ergebnis ist der Rest, nachdem `number1` durch dividiert wurde `number2` .</span><span class="sxs-lookup"><span data-stu-id="f2b43-116">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="f2b43-117">Beispielsweise wird der Ausdruck `14 Mod 4` zu 2 ausgewertet.</span><span class="sxs-lookup"><span data-stu-id="f2b43-117">For example, the expression `14 Mod 4` evaluates to 2.</span></span>

> [!NOTE]
> <span data-ttu-id="f2b43-118">Es gibt einen Unterschied zwischen *Rest* und *Modulo* in der Mathematik mit unterschiedlichen Ergebnissen für negative Zahlen.</span><span class="sxs-lookup"><span data-stu-id="f2b43-118">There is a difference between *remainder* and *modulus* in mathematics, with different results for negative numbers.</span></span> <span data-ttu-id="f2b43-119">Der `Mod` Operator in Visual Basic, der .NET Framework `op_Modulus` -Operator und die zugrunde liegende [REM](<xref:System.Reflection.Emit.OpCodes.Rem>) Il-Anweisung führen einen Rest-Vorgang aus.</span><span class="sxs-lookup"><span data-stu-id="f2b43-119">The `Mod` operator in Visual Basic, the .NET Framework `op_Modulus` operator, and the underlying [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL instruction all perform a remainder operation.</span></span>

<span data-ttu-id="f2b43-120">Das Ergebnis eines- `Mod` Vorgangs behält das Vorzeichen der Dividende bei, `number1` und es kann positiv oder negativ sein.</span><span class="sxs-lookup"><span data-stu-id="f2b43-120">The result of a `Mod` operation retains the sign of the dividend, `number1`, and so it may be positive or negative.</span></span> <span data-ttu-id="f2b43-121">Das Ergebnis liegt immer im Bereich (- `number2` , `number2` ), exklusiv.</span><span class="sxs-lookup"><span data-stu-id="f2b43-121">The result is always in the range (-`number2`, `number2`), exclusive.</span></span> <span data-ttu-id="f2b43-122">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="f2b43-122">For example:</span></span>

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a><span data-ttu-id="f2b43-123">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="f2b43-123">Remarks</span></span>

<span data-ttu-id="f2b43-124">Wenn entweder `number1` oder `number2` ein Gleit Komma Wert ist, wird der Rest der Division zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="f2b43-124">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="f2b43-125">Der Datentyp des Ergebnisses ist der kleinste Datentyp, der alle möglichen Werte enthalten kann, die sich aus der Division mit den Datentypen `number1` und ergeben `number2` .</span><span class="sxs-lookup"><span data-stu-id="f2b43-125">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>

<span data-ttu-id="f2b43-126">Wenn `number1` oder `number2` als " [Nothing](../nothing.md)" ausgewertet wird, wird es als 0 (null) behandelt.</span><span class="sxs-lookup"><span data-stu-id="f2b43-126">If `number1` or `number2` evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>

<span data-ttu-id="f2b43-127">Verwandte Operatoren umfassen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="f2b43-127">Related operators include the following:</span></span>

- <span data-ttu-id="f2b43-128">Der [Operator \ (Visual Basic)](integer-division-operator.md) gibt den ganzzahligen Quotienten einer Division zurück.</span><span class="sxs-lookup"><span data-stu-id="f2b43-128">The [\ Operator (Visual Basic)](integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="f2b43-129">Der Ausdruck wird z `14 \ 4` . b. zu 3 ausgewertet.</span><span class="sxs-lookup"><span data-stu-id="f2b43-129">For example, the expression `14 \ 4` evaluates to 3.</span></span>

- <span data-ttu-id="f2b43-130">Der [Operator/(Visual Basic)](floating-point-division-operator.md) gibt den vollständigen Quotienten, einschließlich des Restwerts, als Gleit Komma Zahl zurück.</span><span class="sxs-lookup"><span data-stu-id="f2b43-130">The [/ Operator (Visual Basic)](floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="f2b43-131">Der Ausdruck wird z `14 / 4` . b. zu 3,5 ausgewertet.</span><span class="sxs-lookup"><span data-stu-id="f2b43-131">For example, the expression `14 / 4` evaluates to 3.5.</span></span>

## <a name="attempted-division-by-zero"></a><span data-ttu-id="f2b43-132">Versuchte Division durch Null</span><span class="sxs-lookup"><span data-stu-id="f2b43-132">Attempted division by zero</span></span>

<span data-ttu-id="f2b43-133">Wenn der Wert 0 (null) ergibt `number2` , hängt das Verhalten des- `Mod` Operators vom Datentyp der Operanden ab:</span><span class="sxs-lookup"><span data-stu-id="f2b43-133">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands:</span></span>

- <span data-ttu-id="f2b43-134">Eine ganzzahlige Division löst eine <xref:System.DivideByZeroException> -Ausnahme aus, wenn `number2` nicht in der Kompilierzeit bestimmt werden kann, und generiert einen Kompilierzeitfehler `BC30542 Division by zero occurred while evaluating this expression` `number2` , wenn zur Kompilierzeit NULL ergibt.</span><span class="sxs-lookup"><span data-stu-id="f2b43-134">An integral division throws a <xref:System.DivideByZeroException> exception if `number2` cannot be determined in compile-time and generates a compile-time error `BC30542 Division by zero occurred while evaluating this expression` if `number2` is evaluated to zero at compile-time.</span></span>
- <span data-ttu-id="f2b43-135">Eine Gleit Komma Division gibt zurück <xref:System.Double.NaN?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f2b43-135">A floating-point division returns <xref:System.Double.NaN?displayProperty=nameWithType>.</span></span>

## <a name="equivalent-formula"></a><span data-ttu-id="f2b43-136">Äquivalente Formel</span><span class="sxs-lookup"><span data-stu-id="f2b43-136">Equivalent formula</span></span>

<span data-ttu-id="f2b43-137">Der Ausdruck `a Mod b` entspricht einer der folgenden Formeln:</span><span class="sxs-lookup"><span data-stu-id="f2b43-137">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>

`a - (b * (a \ b))`

`a - (b * Fix(a / b))`

## <a name="floating-point-imprecision"></a><span data-ttu-id="f2b43-138">Ungenauigkeit von Gleit Komma Werten</span><span class="sxs-lookup"><span data-stu-id="f2b43-138">Floating-point imprecision</span></span>

<span data-ttu-id="f2b43-139">Beachten Sie beim Arbeiten mit Gleit Komma Zahlen, dass Sie nicht immer über eine genaue Dezimal Darstellung im Arbeitsspeicher verfügen.</span><span class="sxs-lookup"><span data-stu-id="f2b43-139">When you work with floating-point numbers, remember that they do not always have a precise decimal representation in memory.</span></span> <span data-ttu-id="f2b43-140">Dies kann zu unerwarteten Ergebnissen von bestimmten Vorgängen führen, wie z. b. Wert Vergleiche und `Mod` Operator.</span><span class="sxs-lookup"><span data-stu-id="f2b43-140">This can lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="f2b43-141">Weitere Informationen finden Sie unter [Problembehandlung bei Datentypen](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="f2b43-141">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

## <a name="overloading"></a><span data-ttu-id="f2b43-142">Überladen</span><span class="sxs-lookup"><span data-stu-id="f2b43-142">Overloading</span></span>

<span data-ttu-id="f2b43-143">Der `Mod` Operator kann *überladen*werden, was bedeutet, dass eine Klasse oder Struktur das Verhalten neu definieren kann.</span><span class="sxs-lookup"><span data-stu-id="f2b43-143">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="f2b43-144">Wenn Ihr Code `Mod` auf eine Instanz einer Klasse oder Struktur angewendet wird, die eine solche Überlastung einschließt, stellen Sie sicher, dass Sie das neu definierte Verhalten verstehen.</span><span class="sxs-lookup"><span data-stu-id="f2b43-144">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f2b43-145">Weitere Informationen finden Sie unter [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f2b43-145">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="example"></a><span data-ttu-id="f2b43-146">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f2b43-146">Example</span></span>

<span data-ttu-id="f2b43-147">Im folgenden Beispiel wird der `Mod` -Operator verwendet, um zwei Zahlen aufzuteilen und nur den Rest zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="f2b43-147">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="f2b43-148">Wenn eine der Zahlen eine Gleit Komma Zahl ist, ist das Ergebnis eine Gleit Komma Zahl, die den Restwert darstellt.</span><span class="sxs-lookup"><span data-stu-id="f2b43-148">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>

[!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]

## <a name="example"></a><span data-ttu-id="f2b43-149">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f2b43-149">Example</span></span>

<span data-ttu-id="f2b43-150">Im folgenden Beispiel wird die mögliche Ungenauigkeit von Gleit Komma Operanden veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="f2b43-150">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="f2b43-151">In der ersten Anweisung sind die Operanden `Double` , und 0,2 ist ein unendlich wiederholter binärer Bruchteil mit einem gespeicherten Wert von 0.20000000000000001.</span><span class="sxs-lookup"><span data-stu-id="f2b43-151">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="f2b43-152">In der zweiten Anweisung erzwingt das Literaltypzeichen `D` beide Operanden zu `Decimal` , und 0,2 hat eine genaue Darstellung.</span><span class="sxs-lookup"><span data-stu-id="f2b43-152">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>

[!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]

## <a name="see-also"></a><span data-ttu-id="f2b43-153">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f2b43-153">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [<span data-ttu-id="f2b43-154">Arithmetische Operatoren</span><span class="sxs-lookup"><span data-stu-id="f2b43-154">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="f2b43-155">Operatorrangfolge in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f2b43-155">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="f2b43-156">Nach Funktionalität sortierte Operatoren</span><span class="sxs-lookup"><span data-stu-id="f2b43-156">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="f2b43-157">Problembehandlung bei Datentypen</span><span class="sxs-lookup"><span data-stu-id="f2b43-157">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="f2b43-158">Arithmetische Operatoren in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f2b43-158">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="f2b43-159">\-Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2b43-159">\ Operator (Visual Basic)</span></span>](integer-division-operator.md)
