---
title: Übergeben von Argumenten nach Position und Name
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
ms.openlocfilehash: 686b64977f086c8128e56298a0ed8c5aa0c51efa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364031"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="27137-102">Übergeben von Argumenten nach Position und Name (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27137-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>

<span data-ttu-id="27137-103">Wenn Sie eine- `Sub` oder `Function` -Prozedur aufzurufen, können Sie Argumente *nach Position* – in der Reihenfolge übergeben, in der Sie in der Definition der Prozedur angezeigt werden – oder Sie können Sie ohne Berücksichtigung der Position *nach Namen*übergeben.</span><span class="sxs-lookup"><span data-stu-id="27137-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>

<span data-ttu-id="27137-104">Wenn Sie ein Argument anhand des Namens übergeben, geben Sie den deklarierten Namen des Arguments an, gefolgt von einem Doppelpunkt und einem Gleichheitszeichen ( `:=` ), gefolgt vom Argument Wert.</span><span class="sxs-lookup"><span data-stu-id="27137-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="27137-105">Sie können benannte Argumente in beliebiger Reihenfolge angeben.</span><span class="sxs-lookup"><span data-stu-id="27137-105">You can supply named arguments in any order.</span></span>

<span data-ttu-id="27137-106">Beispielsweise werden im folgenden `Sub` Verfahren drei Argumente benötigt:</span><span class="sxs-lookup"><span data-stu-id="27137-106">For example, the following `Sub` procedure takes three arguments:</span></span>

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

<span data-ttu-id="27137-107">Wenn Sie diese Prozedur aufzurufen, können Sie die Argumente nach Position, Name oder mithilfe einer Kombination aus beidem bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="27137-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>

## <a name="passing-arguments-by-position"></a><span data-ttu-id="27137-108">Übergeben von Argumenten nach Position</span><span class="sxs-lookup"><span data-stu-id="27137-108">Passing Arguments by Position</span></span>

<span data-ttu-id="27137-109">Sie können die `Display` -Methode mit den als Position weiter gegebenen Argumenten und durch Kommas getrennt, wie im folgenden Beispiel gezeigt:</span><span class="sxs-lookup"><span data-stu-id="27137-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

<span data-ttu-id="27137-110">Wenn Sie ein optionales Argument in einer Liste von Positions Argumenten weglassen, müssen Sie den Platz mit einem Komma ablegen.</span><span class="sxs-lookup"><span data-stu-id="27137-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="27137-111">Im folgenden Beispiel wird die- `Display` Methode ohne das- `age` Argument aufgerufen:</span><span class="sxs-lookup"><span data-stu-id="27137-111">The following example calls the `Display` method without the `age` argument:</span></span>

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a><span data-ttu-id="27137-112">Übergeben von Argumenten nach Name</span><span class="sxs-lookup"><span data-stu-id="27137-112">Passing Arguments by Name</span></span>

<span data-ttu-id="27137-113">Alternativ können Sie `Display` mit den über den Namen weiter gegebenen Argumenten auch durch Kommas getrennt werden, wie im folgenden Beispiel gezeigt:</span><span class="sxs-lookup"><span data-stu-id="27137-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

<span data-ttu-id="27137-114">Das übergeben von Argumenten nach Namen auf diese Weise ist besonders nützlich, wenn Sie eine Prozedur mit mehr als einem optionalen Argument aufgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="27137-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="27137-115">Wenn Sie Argumente nach Namen angeben, müssen Sie keine aufeinander folgenden Kommas verwenden, um fehlende Positions Argumente anzugeben.</span><span class="sxs-lookup"><span data-stu-id="27137-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="27137-116">Durch die Übergabe von Argumenten nach Name können Sie auch leichter nachverfolgen, welche Argumente Sie übergeben und welche nicht.</span><span class="sxs-lookup"><span data-stu-id="27137-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>

## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="27137-117">Mischen von Argumenten nach Position und Name</span><span class="sxs-lookup"><span data-stu-id="27137-117">Mixing Arguments by Position and by Name</span></span>

<span data-ttu-id="27137-118">Sie können Argumente sowohl nach Position als auch nach Name in einem einzelnen Prozedur Befehl angeben, wie im folgenden Beispiel gezeigt:</span><span class="sxs-lookup"><span data-stu-id="27137-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

<span data-ttu-id="27137-119">Im vorherigen Beispiel ist kein zusätzliches Komma erforderlich, um die Position des ausgelassenen Arguments aufzunehmen `age` , da `birth` nach Name übermittelt wird.</span><span class="sxs-lookup"><span data-stu-id="27137-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>

<span data-ttu-id="27137-120">Wenn Sie in Versionen von Visual Basic vor 15,5, wenn Sie Argumente durch eine Mischung aus Position und Name angeben, müssen die Positions Argumente zuerst alle auftreten.</span><span class="sxs-lookup"><span data-stu-id="27137-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="27137-121">Nachdem Sie ein Argument nach Namen angegeben haben, müssen alle verbleibenden Argumente als Name übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="27137-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="27137-122">Der folgende Aufrufe der- `Display` Methode zeigt z. b. Compilerfehler [BC30241: das benannte Argument wurde erwartet](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="27137-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

<span data-ttu-id="27137-123">Ab Visual Basic 15,5 können Positions Argumente benannte Argumente folgen, wenn sich die abschließenden Positions Argumente an der richtigen Position befinden.</span><span class="sxs-lookup"><span data-stu-id="27137-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="27137-124">Bei der Kompilierung unter Visual Basic 15,5 wird der vorherige-Befehl der `Display` -Methode erfolgreich kompiliert und generiert den Compilerfehler [BC30241](../../../misc/bc30241.md)nicht mehr.</span><span class="sxs-lookup"><span data-stu-id="27137-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>

<span data-ttu-id="27137-125">Diese Möglichkeit, benannte und Positions Argumente in beliebiger Reihenfolge zu mischen und abzugleichen, ist besonders nützlich, wenn Sie ein benanntes Argument verwenden möchten, um den Code lesbarer zu machen.</span><span class="sxs-lookup"><span data-stu-id="27137-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="27137-126">Der folgende `Person` Klassenkonstruktor benötigt z. b. zwei Argumente des-Typs `Person` , die beide sein können `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="27137-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

<span data-ttu-id="27137-127">Wenn Sie gemischte benannte und Positions Argumente verwenden, ist es hilfreich, den Zweck des Codes klar zu machen, wenn der Wert des `father` -Arguments und des- `mother` Arguments lautet `Nothing` :</span><span class="sxs-lookup"><span data-stu-id="27137-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

<span data-ttu-id="27137-128">Wenn Sie Positions Argumenten mit benannten Argumenten folgen möchten, müssen Sie das folgende-Element der Visual Basic Project- \* Datei (. vbproj) hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="27137-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="27137-129">Weitere Informationen finden Sie [unter Festlegen der Visual Basic Sprachversion](../../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="27137-129">For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="27137-130">Einschränkungen beim Bereitstellen von Argumenten nach Namen</span><span class="sxs-lookup"><span data-stu-id="27137-130">Restrictions on Supplying Arguments by Name</span></span>

<span data-ttu-id="27137-131">Sie können keine Argumente nach Namen übergeben, um zu vermeiden, dass erforderliche Argumente eingegeben werden.</span><span class="sxs-lookup"><span data-stu-id="27137-131">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="27137-132">Sie können nur die optionalen Argumente weglassen.</span><span class="sxs-lookup"><span data-stu-id="27137-132">You can omit only the optional arguments.</span></span>

<span data-ttu-id="27137-133">Ein Parameter Array kann nicht anhand des Namens übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="27137-133">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="27137-134">Dies liegt daran, dass beim Aufrufen der Prozedur eine unbegrenzte Anzahl von Komma getrennten Argumenten für das Parameter Array bereitgestellt wird, und der Compiler kann nicht mehr als ein Argument mit einem einzelnen Namen zuordnen.</span><span class="sxs-lookup"><span data-stu-id="27137-134">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>

## <a name="see-also"></a><span data-ttu-id="27137-135">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="27137-135">See also</span></span>

- [<span data-ttu-id="27137-136">Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="27137-136">Procedures</span></span>](./index.md)
- [<span data-ttu-id="27137-137">Parameter und Argumente von Prozeduren</span><span class="sxs-lookup"><span data-stu-id="27137-137">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="27137-138">Vorgehensweise: Übergeben von Argumenten an eine Prozedur</span><span class="sxs-lookup"><span data-stu-id="27137-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="27137-139">Übergeben von Argumenten als Wert und als Verweis</span><span class="sxs-lookup"><span data-stu-id="27137-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="27137-140">Optionale Parameter</span><span class="sxs-lookup"><span data-stu-id="27137-140">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="27137-141">Parameter Arrays</span><span class="sxs-lookup"><span data-stu-id="27137-141">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="27137-142">Optional</span><span class="sxs-lookup"><span data-stu-id="27137-142">Optional</span></span>](../../../language-reference/modifiers/optional.md)
- [<span data-ttu-id="27137-143">ParamArray</span><span class="sxs-lookup"><span data-stu-id="27137-143">ParamArray</span></span>](../../../language-reference/modifiers/paramarray.md)
