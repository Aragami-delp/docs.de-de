---
title: Bewährte Methoden zum Schreiben von Komponententests
description: Erfahren Sie mehr über bewährte Methoden zum Schreiben von Komponententests, die die Qualität und Stabilität von Code für .NET Core- und .NET Standard-Projekte gewährleisten.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.openlocfilehash: ffeaa1e11512cab64695c120f844594b8c5014a8
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281107"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a><span data-ttu-id="60ee8-103">Bewährte Methoden für Komponententests mit .NET Core und .NET Standard</span><span class="sxs-lookup"><span data-stu-id="60ee8-103">Unit testing best practices with .NET Core and .NET Standard</span></span>

<span data-ttu-id="60ee8-104">Komponententests bringen zahlreiche Vorteile mit sich: Sie helfen bei der Regression, stellen Dokumentation bereit und unterstützen Sie beim Entwerfen guten Codes.</span><span class="sxs-lookup"><span data-stu-id="60ee8-104">There are numerous benefits to writing unit tests; they help with regression, provide documentation, and facilitate good design.</span></span> <span data-ttu-id="60ee8-105">Allerdings können Komponententest, die schwierig zu lesen und fehleranfällig sind, zu einer unübersichtlichen Codebasis führen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-105">However, hard to read and brittle unit tests can wreak havoc on your code base.</span></span> <span data-ttu-id="60ee8-106">In diesem Artikel werden einige bewährte Methoden in Bezug auf den Entwurf von Komponententests für Ihre .NET Core- und .NET Standard-Projekte beschrieben.</span><span class="sxs-lookup"><span data-stu-id="60ee8-106">This article describes some best practices regarding unit test design for your .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="60ee8-107">In diesem Leitfaden lernen Sie die bewährten Methoden beim Schreiben von Komponententests kennen, mit denen Sie Ihre Tests resilient und leicht verständlich gestalten können.</span><span class="sxs-lookup"><span data-stu-id="60ee8-107">In this guide, you'll learn some best practices when writing unit tests to keep your tests resilient and easy to understand.</span></span>

<span data-ttu-id="60ee8-108">Von [John Reese](https://reese.dev) mit besonderem Dank an [Roy Osherove](https://osherove.com/)</span><span class="sxs-lookup"><span data-stu-id="60ee8-108">By [John Reese](https://reese.dev) with special thanks to [Roy Osherove](https://osherove.com/)</span></span>

## <a name="why-unit-test"></a><span data-ttu-id="60ee8-109">Weshalb sollte ich Komponententests durchführen?</span><span class="sxs-lookup"><span data-stu-id="60ee8-109">Why unit test?</span></span>

### <a name="less-time-performing-functional-tests"></a><span data-ttu-id="60ee8-110">Weniger Zeitaufwand für das Ausführen von Funktionstests</span><span class="sxs-lookup"><span data-stu-id="60ee8-110">Less time performing functional tests</span></span>

<span data-ttu-id="60ee8-111">Funktionstests sind kostspielig.</span><span class="sxs-lookup"><span data-stu-id="60ee8-111">Functional tests are expensive.</span></span> <span data-ttu-id="60ee8-112">Für Funktionstests muss normalerweise die Anwendung geöffnet werden, und Sie (oder eine andere Person) müssen mehrere Schritte ausführen, um das erwartete Verhalten zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-112">They typically involve opening up the application and performing a series of steps that you (or someone else), must follow in order to validate the expected behavior.</span></span> <span data-ttu-id="60ee8-113">Es kann durchaus sein, dass der Tester diese Schritte nicht kennt, was bedeutet, dass sich dieser an eine Person wenden muss, die sich in dem Bereich auskennt, um den Test auszuführen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-113">These steps may not always be known to the tester, which means they will have to reach out to someone more knowledgeable in the area in order to carry out the test.</span></span> <span data-ttu-id="60ee8-114">Der Testvorgang selbst kann nur ein paar Sekunden für banale Änderungen oder Minuten für größere Änderungen in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-114">Testing itself could take seconds for trivial changes, or minutes for larger changes.</span></span> <span data-ttu-id="60ee8-115">Abschließend muss der ganze Vorgang für jede Änderung, die Sie am System vornehmen, wiederholt werden.</span><span class="sxs-lookup"><span data-stu-id="60ee8-115">Lastly, this process must be repeated for every change that you make in the system.</span></span>

<span data-ttu-id="60ee8-116">Im Vergleich dazu benötigen Komponententests nur Millisekunden. Außerdem können sie durch einen Klick auf eine Schaltfläche ausgeführt werden und erfordern keine tiefgreifenden Kenntnisse zum System.</span><span class="sxs-lookup"><span data-stu-id="60ee8-116">Unit tests, on the other hand, take milliseconds, can be run at the press of a button, and don't necessarily require any knowledge of the system at large.</span></span> <span data-ttu-id="60ee8-117">Ob der Test erfolgreich ist oder fehlschlägt, hängt vom Testlauf und nicht von der einzelnen Person ab, die den Test ausführt.</span><span class="sxs-lookup"><span data-stu-id="60ee8-117">Whether or not the test passes or fails is up to the test runner, not the individual.</span></span>

### <a name="protection-against-regression"></a><span data-ttu-id="60ee8-118">Schutz vor Regression</span><span class="sxs-lookup"><span data-stu-id="60ee8-118">Protection against regression</span></span>

<span data-ttu-id="60ee8-119">Regressionsfehler sind Fehler, die auftreten, wenn eine Änderung an der Anwendung vorgenommen wird.</span><span class="sxs-lookup"><span data-stu-id="60ee8-119">Regression defects are defects that are introduced when a change is made to the application.</span></span> <span data-ttu-id="60ee8-120">Tester testen meist nicht nur ihr neues Feature sondern auch die Features, die zuvor schon vorhanden waren. So können sie überprüfen, ob die zuvor implementierten Features noch immer wie erwartet funktionieren.</span><span class="sxs-lookup"><span data-stu-id="60ee8-120">It is common for testers to not only test their new feature but also features that existed beforehand in order to verify that previously implemented features still function as expected.</span></span>

<span data-ttu-id="60ee8-121">Durch Komponententests ist es möglich, die gesamte Testsammlung nach jedem Build oder sogar nach jeder Änderung an einer Codezeile erneut durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-121">With unit testing, it's possible to rerun your entire suite of tests after every build or even after you change a line of code.</span></span> <span data-ttu-id="60ee8-122">So können Sie sicherstellen, dass Ihr neuer Code die vorhandene Funktionalität nicht beeinträchtigt.</span><span class="sxs-lookup"><span data-stu-id="60ee8-122">Giving you confidence that your new code does not break existing functionality.</span></span>

### <a name="executable-documentation"></a><span data-ttu-id="60ee8-123">Dokumentation zur Ausführbarkeit</span><span class="sxs-lookup"><span data-stu-id="60ee8-123">Executable documentation</span></span>

<span data-ttu-id="60ee8-124">Es ist nicht immer offensichtlich, was genau eine bestimmte Methode tut oder wie sie sich bei einer bestimmten Eingabe verhält.</span><span class="sxs-lookup"><span data-stu-id="60ee8-124">It may not always be obvious what a particular method does or how it behaves given a certain input.</span></span> <span data-ttu-id="60ee8-125">Sie fragen sich vielleicht: Wie verhält sich diese Methode, wenn ich ihr eine leere Zeichenfolge übergebe?</span><span class="sxs-lookup"><span data-stu-id="60ee8-125">You may ask yourself: How does this method behave if I pass it a blank string?</span></span> <span data-ttu-id="60ee8-126">Oder was geschieht, wenn ich NULL übergebe?</span><span class="sxs-lookup"><span data-stu-id="60ee8-126">Null?</span></span>

<span data-ttu-id="60ee8-127">Wenn Sie über eine Sammlung von sinnvoll benannten Komponententests verfügen, sollte jeder Test die erwartete Ausgabe für eine gegebene Eingabe eindeutig erklären können.</span><span class="sxs-lookup"><span data-stu-id="60ee8-127">When you have a suite of well-named unit tests, each test should be able to clearly explain the expected output for a given input.</span></span> <span data-ttu-id="60ee8-128">Zusätzlich sollte er überprüfen, ob sie tatsächlich funktioniert.</span><span class="sxs-lookup"><span data-stu-id="60ee8-128">In addition, it should be able to verify that it actually works.</span></span>

### <a name="less-coupled-code"></a><span data-ttu-id="60ee8-129">Weniger gekoppelter Code</span><span class="sxs-lookup"><span data-stu-id="60ee8-129">Less coupled code</span></span>

<span data-ttu-id="60ee8-130">Wenn Code eng gekoppelt ist, kann es schwierig sein, Komponententests dafür auszuführen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-130">When code is tightly coupled, it can be difficult to unit test.</span></span> <span data-ttu-id="60ee8-131">Ohne das Erstellen von Komponententests für den von Ihnen geschriebenen Code kann die Kopplung weniger offensichtlich sein.</span><span class="sxs-lookup"><span data-stu-id="60ee8-131">Without creating unit tests for the code that you're writing, coupling may be less apparent.</span></span>

<span data-ttu-id="60ee8-132">Wenn Sie Tests für Ihren Code schreiben, wird dieser automatisch entkoppelt, da es ansonsten schwieriger wäre, diesen zu testen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-132">Writing tests for your code will naturally decouple your code, because it would be more difficult to test otherwise.</span></span>

## <a name="characteristics-of-a-good-unit-test"></a><span data-ttu-id="60ee8-133">Merkmale eines guten Komponententests</span><span class="sxs-lookup"><span data-stu-id="60ee8-133">Characteristics of a good unit test</span></span>

- <span data-ttu-id="60ee8-134">**Schnelligkeit**.</span><span class="sxs-lookup"><span data-stu-id="60ee8-134">**Fast**.</span></span> <span data-ttu-id="60ee8-135">Es ist nicht ungewöhnlich, dass ausgereifte Projekte Tausende von Komponententests enthalten.</span><span class="sxs-lookup"><span data-stu-id="60ee8-135">It is not uncommon for mature projects to have thousands of unit tests.</span></span> <span data-ttu-id="60ee8-136">Die Ausführung von Komponententests sollte sehr wenig Zeit in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-136">Unit tests should take very little time to run.</span></span> <span data-ttu-id="60ee8-137">Sie sollten innerhalb von Millisekunden abgeschlossen sein.</span><span class="sxs-lookup"><span data-stu-id="60ee8-137">Milliseconds.</span></span>
- <span data-ttu-id="60ee8-138">**Unabhängigkeit**.</span><span class="sxs-lookup"><span data-stu-id="60ee8-138">**Isolated**.</span></span> <span data-ttu-id="60ee8-139">Komponententest sind eigenständig, sie können isoliert ausgeführt werden und verfügen über keine Abhängigkeiten auf externen Faktoren, wie etwa einem Dateisystem oder einer Datenbank.</span><span class="sxs-lookup"><span data-stu-id="60ee8-139">Unit tests are standalone, can be run in isolation, and have no dependencies on any outside factors such as a file system or database.</span></span>
- <span data-ttu-id="60ee8-140">**Wiederholbarkeit**.</span><span class="sxs-lookup"><span data-stu-id="60ee8-140">**Repeatable**.</span></span> <span data-ttu-id="60ee8-141">Das Ausführen eines Komponententests sollte immer zu den gleichen Ergebnissen führen. Wenn Sie zwischen den Ausführungen nichts ändern, sollte sich das Ergebnis auch nicht ändern.</span><span class="sxs-lookup"><span data-stu-id="60ee8-141">Running a unit test should be consistent with its results, that is, it always returns the same result if you do not change anything in between runs.</span></span>
- <span data-ttu-id="60ee8-142">**Selbstprüfung**.</span><span class="sxs-lookup"><span data-stu-id="60ee8-142">**Self-Checking**.</span></span> <span data-ttu-id="60ee8-143">Der Test sollte in der Lage sein, automatisch und ohne menschliches Eingreifen zu erkennen, ob er erfolgreich war oder fehlgeschlagen ist.</span><span class="sxs-lookup"><span data-stu-id="60ee8-143">The test should be able to automatically detect if it passed or failed without any human interaction.</span></span>
- <span data-ttu-id="60ee8-144">**Verhältnismäßigkeit**.</span><span class="sxs-lookup"><span data-stu-id="60ee8-144">**Timely**.</span></span> <span data-ttu-id="60ee8-145">Ein Komponententest darf verglichen mit dem zu testenden Code nicht unverhältnismäßig lang für das Schreiben benötigen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-145">A unit test should not take a disproportionately long time to write compared to the code being tested.</span></span> <span data-ttu-id="60ee8-146">Wenn Sie bemerken, dass der Codetest im Vergleich zum Schreiben des Codes viel Zeit in Anspruch nimmt, erwägen Sie einen Entwurf, der besser getestet werden kann.</span><span class="sxs-lookup"><span data-stu-id="60ee8-146">If you find testing the code taking a large amount of time compared to writing the code, consider a design that is more testable.</span></span>

## <a name="code-coverage"></a><span data-ttu-id="60ee8-147">Codeabdeckung</span><span class="sxs-lookup"><span data-stu-id="60ee8-147">Code coverage</span></span>

<span data-ttu-id="60ee8-148">Ein hoher Code-Coverage-Prozentsatz steht oft im Zusammenhang mit einer höheren Codequalität.</span><span class="sxs-lookup"><span data-stu-id="60ee8-148">A high code coverage percentage is often associated with a higher quality of code.</span></span> <span data-ttu-id="60ee8-149">Durch die Messung an sich kann die Codequalität jedoch *nicht* bestimmt werden.</span><span class="sxs-lookup"><span data-stu-id="60ee8-149">However, the measurement itself *cannot* determine the quality of code.</span></span> <span data-ttu-id="60ee8-150">Das Festlegen eines übermäßig ambitionierten Code-Coverage-Prozentsatzes kann kontraproduktiv sein.</span><span class="sxs-lookup"><span data-stu-id="60ee8-150">Setting an overly ambitious code coverage percentage goal can be counterproductive.</span></span> <span data-ttu-id="60ee8-151">Stellen Sie sich ein komplexes Projekt mit Tausenden von bedingten Branches vor, und stellen Sie sich vor, dass Sie ein Code-Coverage-Ziel von 95 % festlegen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-151">Imagine a complex project with thousands of conditional branches, and imagine that you set a goal of 95% code coverage.</span></span> <span data-ttu-id="60ee8-152">Derzeit weist das Projekt 90 % Code Coverage auf.</span><span class="sxs-lookup"><span data-stu-id="60ee8-152">Currently the project maintains 90% code coverage.</span></span> <span data-ttu-id="60ee8-153">Für die restlichen 5 % könnte für alle Grenzfälle sehr viel Zeit einkalkuliert werden müssen, und der Wertbeitrag verringert sich schnell.</span><span class="sxs-lookup"><span data-stu-id="60ee8-153">The amount of time it takes to account for all of the edge cases in the remaining 5% could be a massive undertaking, and the value proposition quickly diminishes.</span></span>

<span data-ttu-id="60ee8-154">Ein hoher Code-Coverage-Prozentsatz ist weder ein Erfolgsindikator noch ein Hinweis auf eine hohe Codequalität.</span><span class="sxs-lookup"><span data-stu-id="60ee8-154">A high code coverage percentage is not an indicator of success, nor does it imply high code quality.</span></span> <span data-ttu-id="60ee8-155">Er stellt lediglich die Menge an Code dar, die durch Komponententests abgedeckt wird.</span><span class="sxs-lookup"><span data-stu-id="60ee8-155">It just represents the amount of code that is covered by unit tests.</span></span> <span data-ttu-id="60ee8-156">Weitere Informationen finden Sie unter [Verwenden von Code Coverage für Komponententests](unit-testing-code-coverage.md).</span><span class="sxs-lookup"><span data-stu-id="60ee8-156">For more information, see [unit testing code coverage](unit-testing-code-coverage.md).</span></span>

## <a name="lets-speak-the-same-language"></a><span data-ttu-id="60ee8-157">Begriffsklärung</span><span class="sxs-lookup"><span data-stu-id="60ee8-157">Let's speak the same language</span></span>

<span data-ttu-id="60ee8-158">Der Begriff *Mock* (Deutsch: „Pseudo“) wird leider im Testkontext häufig falsch verwendet.</span><span class="sxs-lookup"><span data-stu-id="60ee8-158">The term *mock* is unfortunately often misused when talking about testing.</span></span> <span data-ttu-id="60ee8-159">Im Folgenden werden die häufigsten Arten von unechten Objekten, sogenannten *Fakes*, beim Schreiben von Komponententests definiert:</span><span class="sxs-lookup"><span data-stu-id="60ee8-159">The following points define the most common types of *fakes* when writing unit tests:</span></span>

<span data-ttu-id="60ee8-160">*Fake*: Fake ist ein generischer Begriff, der sowohl für Stubs als auch für Pseudoobjekte („Mocks“) verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="60ee8-160">*Fake* - A fake is a generic term that can be used to describe either a stub or a mock object.</span></span> <span data-ttu-id="60ee8-161">Ob es sich um einen Stub oder um einen Mock handelt, hängt vom Kontext ab.</span><span class="sxs-lookup"><span data-stu-id="60ee8-161">Whether it's a stub or a mock depends on the context in which it's used.</span></span> <span data-ttu-id="60ee8-162">Das bedeutet, dass ein Fake entweder ein Stub oder ein Mock sein kann.</span><span class="sxs-lookup"><span data-stu-id="60ee8-162">So in other words, a fake can be a stub or a mock.</span></span>

<span data-ttu-id="60ee8-163">*Mock*: Ein Pseudoobjekt ist ein unechtes Objekt im System, das entscheidet, ob ein Komponententest erfolgreich war oder nicht.</span><span class="sxs-lookup"><span data-stu-id="60ee8-163">*Mock* - A mock object is a fake object in the system that decides whether or not a unit test has passed or failed.</span></span> <span data-ttu-id="60ee8-164">Ein Mock ist zunächst ein Fake, bis eine Assert-Anweisung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="60ee8-164">A mock starts out as a Fake until it's asserted against.</span></span>

<span data-ttu-id="60ee8-165">*Stub*: Ein Stub ist ein anpassbarer Platzhalter für eine vorhandene Abhängigkeit (oder einen Projektmitarbeiter) im System.</span><span class="sxs-lookup"><span data-stu-id="60ee8-165">*Stub* - A stub is a controllable replacement for an existing dependency (or collaborator) in the system.</span></span> <span data-ttu-id="60ee8-166">Wenn Sie einen Stub verwenden, können Sie Ihren Code testen, ohne sich direkt um die Abhängigkeit kümmern zu müssen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-166">By using a stub, you can test your code without dealing with the dependency directly.</span></span> <span data-ttu-id="60ee8-167">Standardmäßig ist ein Fake immer zunächst ein Stub.</span><span class="sxs-lookup"><span data-stu-id="60ee8-167">By default, a fake starts out as a stub.</span></span>

<span data-ttu-id="60ee8-168">Betrachten Sie den folgenden Codeausschnitt:</span><span class="sxs-lookup"><span data-stu-id="60ee8-168">Consider the following code snippet:</span></span>

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="60ee8-169">Dies wäre ein Beispiel eines Stubs, der als Mock bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="60ee8-169">This would be an example of stub being referred to as a mock.</span></span> <span data-ttu-id="60ee8-170">In diesem Fall handelt es sich aber um einen Stub.</span><span class="sxs-lookup"><span data-stu-id="60ee8-170">In this case, it is a stub.</span></span> <span data-ttu-id="60ee8-171">Sie übergeben „Order“ nur, um `Purchase` instanziieren zu können (das System, das getestet wird).</span><span class="sxs-lookup"><span data-stu-id="60ee8-171">You're just passing in the Order as a means to be able to instantiate `Purchase` (the system under test).</span></span> <span data-ttu-id="60ee8-172">Die Bezeichnung `MockOrder` ist ebenfalls irreführend, da auch hier die Reihenfolge keinen Mock darstellt.</span><span class="sxs-lookup"><span data-stu-id="60ee8-172">The name `MockOrder` is also misleading because again, the order is not a mock.</span></span>

<span data-ttu-id="60ee8-173">Dies ist ein besserer Ansatz:</span><span class="sxs-lookup"><span data-stu-id="60ee8-173">A better approach would be</span></span>

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="60ee8-174">Indem die Klasse in `FakeOrder` umbenannt wird, wird sie generischer und kann so als Mock oder Stub verwendet werden,</span><span class="sxs-lookup"><span data-stu-id="60ee8-174">By renaming the class to `FakeOrder`, you've made the class a lot more generic, the class can be used as a mock or a stub.</span></span> <span data-ttu-id="60ee8-175">je nachdem, was für die Testsituation besser geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="60ee8-175">Whichever is better for the test case.</span></span> <span data-ttu-id="60ee8-176">Im Beispiel oben wird `FakeOrder` als Stub verwendet.</span><span class="sxs-lookup"><span data-stu-id="60ee8-176">In the above example, `FakeOrder` is used as a stub.</span></span> <span data-ttu-id="60ee8-177">Sie verwenden `FakeOrder` nicht in der Assert-Anweisung.</span><span class="sxs-lookup"><span data-stu-id="60ee8-177">You're not using the `FakeOrder` in any shape or form during the assert.</span></span> <span data-ttu-id="60ee8-178">Die `FakeOrder` wurde nur an die Klasse `Purchase` übergeben, um die Anforderungen des Konstruktors zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-178">`FakeOrder` was passed into the `Purchase` class to satisfy the requirements of the constructor.</span></span>

<span data-ttu-id="60ee8-179">Um „Purchase“ als Mock verwenden zu können, können Sie z.B. wie folgt vorgehen:</span><span class="sxs-lookup"><span data-stu-id="60ee8-179">To use it as a Mock, you could do something like this</span></span>

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

<span data-ttu-id="60ee8-180">In diesem Fall überprüfen Sie eine Eigenschaft des Fakes (d.h. führen eine Assert-Anweisung dafür aus). Im Codeausschnitt oben ist `mockOrder` also ein Mock.</span><span class="sxs-lookup"><span data-stu-id="60ee8-180">In this case, you are checking a property on the Fake (asserting against it), so in the above code snippet, the `mockOrder` is a Mock.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="60ee8-181">Es ist wichtig, dass die Terminologie richtig ist.</span><span class="sxs-lookup"><span data-stu-id="60ee8-181">It's important to get this terminology correct.</span></span> <span data-ttu-id="60ee8-182">Wenn Sie Ihre Stubs als „Mocks“ bezeichnen, können andere Entwickler Ihre Absicht falsch verstehen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-182">If you call your stubs "mocks", other developers are going to make false assumptions about your intent.</span></span>

<span data-ttu-id="60ee8-183">Der Hauptunterschied zwischen Mocks und Stubs ist also der folgende: Mocks unterscheiden sich im Grunde genommen kaum von Stubs, für diese führen Sie aber eine Assert-Anweisung aus, und für einen Stub nicht.</span><span class="sxs-lookup"><span data-stu-id="60ee8-183">The main thing to remember about mocks versus stubs is that mocks are just like stubs, but you assert against the mock object, whereas you do not assert against a stub.</span></span>

## <a name="best-practices"></a><span data-ttu-id="60ee8-184">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="60ee8-184">Best practices</span></span>

### <a name="naming-your-tests"></a><span data-ttu-id="60ee8-185">Benennen Ihrer Tests</span><span class="sxs-lookup"><span data-stu-id="60ee8-185">Naming your tests</span></span>

<span data-ttu-id="60ee8-186">Der Name Ihres Tests sollte aus drei Teilen bestehen:</span><span class="sxs-lookup"><span data-stu-id="60ee8-186">The name of your test should consist of three parts:</span></span>

- <span data-ttu-id="60ee8-187">aus dem Namen der Methode, die getestet wird</span><span class="sxs-lookup"><span data-stu-id="60ee8-187">The name of the method being tested.</span></span>
- <span data-ttu-id="60ee8-188">aus den Bedingungen, unter denen getestet wird</span><span class="sxs-lookup"><span data-stu-id="60ee8-188">The scenario under which it's being tested.</span></span>
- <span data-ttu-id="60ee8-189">aus dem erwarteten Verhalten, wenn das Szenario aufgerufen wird</span><span class="sxs-lookup"><span data-stu-id="60ee8-189">The expected behavior when the scenario is invoked.</span></span>

#### <a name="why"></a><span data-ttu-id="60ee8-190">Warum?</span><span class="sxs-lookup"><span data-stu-id="60ee8-190">Why?</span></span>

- <span data-ttu-id="60ee8-191">Benennungsstandards sind wichtig, da diese die Absicht des Tests explizit ausdrücken.</span><span class="sxs-lookup"><span data-stu-id="60ee8-191">Naming standards are important because they explicitly express the intent of the test.</span></span>

<span data-ttu-id="60ee8-192">Tests sind nicht nur dazu da sicherzustellen, dass Ihr Code funktioniert, sie bieten auch Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="60ee8-192">Tests are more than just making sure your code works, they also provide documentation.</span></span> <span data-ttu-id="60ee8-193">Sie sollten anhand der Komponententestsammlung in der Lage sein, das Verhalten Ihres Codes abzuleiten, auch wenn Sie nicht den Code selbst ansehen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-193">Just by looking at the suite of unit tests, you should be able to infer the behavior of your code without even looking at the code itself.</span></span> <span data-ttu-id="60ee8-194">Wenn Tests fehlschlagen, können Sie zusätzlich genau erkennen, welche Szenarios nicht Ihren Erwartungen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-194">Additionally, when tests fail, you can see exactly which scenarios do not meet your expectations.</span></span>

#### <a name="bad"></a><span data-ttu-id="60ee8-195">Nicht empfohlen:</span><span class="sxs-lookup"><span data-stu-id="60ee8-195">Bad:</span></span>

[!code-csharp[BeforeNaming](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a><span data-ttu-id="60ee8-196">Empfohlen:</span><span class="sxs-lookup"><span data-stu-id="60ee8-196">Better:</span></span>

[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a><span data-ttu-id="60ee8-197">Anordnen Ihrer Tests</span><span class="sxs-lookup"><span data-stu-id="60ee8-197">Arranging your tests</span></span>

<span data-ttu-id="60ee8-198">**Arrange, Act, Assert** ist ein häufiges Muster beim Ausführen von Komponententests.</span><span class="sxs-lookup"><span data-stu-id="60ee8-198">**Arrange, Act, Assert** is a common pattern when unit testing.</span></span> <span data-ttu-id="60ee8-199">Dieses Muster besteht aus drei Hauptteilen:</span><span class="sxs-lookup"><span data-stu-id="60ee8-199">As the name implies, it consists of three main actions:</span></span>

- <span data-ttu-id="60ee8-200">*Arrange*: Ordnen Sie Ihrer Objekte an, und erstellen und planen Sie diese nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="60ee8-200">*Arrange* your objects, creating and setting them up as necessary.</span></span>
- <span data-ttu-id="60ee8-201">*Act*: Führen Sie eine Aktion für ein Objekt durch.</span><span class="sxs-lookup"><span data-stu-id="60ee8-201">*Act* on an object.</span></span>
- <span data-ttu-id="60ee8-202">*Assert*: Überprüfen Sie die ordnungsgemäße Funktionsweise.</span><span class="sxs-lookup"><span data-stu-id="60ee8-202">*Assert* that something is as expected.</span></span>

#### <a name="why"></a><span data-ttu-id="60ee8-203">Warum?</span><span class="sxs-lookup"><span data-stu-id="60ee8-203">Why?</span></span>

- <span data-ttu-id="60ee8-204">Durch diese Methode wird ganz klar unterteilt, was unter den Schritten *arrange* und *assert* getestet wird.</span><span class="sxs-lookup"><span data-stu-id="60ee8-204">Clearly separates what is being tested from the *arrange* and *assert* steps.</span></span>
- <span data-ttu-id="60ee8-205">Es ist weniger wahrscheinlich, dass Überprüfungen mit dem „act“-Code vermischt werden.</span><span class="sxs-lookup"><span data-stu-id="60ee8-205">Less chance to intermix assertions with "Act" code.</span></span>

<span data-ttu-id="60ee8-206">Die Lesbarkeit ist einer der wichtigsten Punkte beim Schreiben eines Tests.</span><span class="sxs-lookup"><span data-stu-id="60ee8-206">Readability is one of the most important aspects when writing a test.</span></span> <span data-ttu-id="60ee8-207">Durch die Aufteilung innerhalb des Tests werden die Abhängigkeiten deutlich, die beim Codeaufruf, der Art und Weise des Codeaufrufs und bei der Überprüfung entstehen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-207">Separating each of these actions within the test clearly highlight the dependencies required to call your code, how your code is being called, and what you are trying to assert.</span></span> <span data-ttu-id="60ee8-208">Einige Schritte können zwar möglicherweise kombiniert werden, wodurch die Größe Ihres Tests verringert wird, jedoch liegt das Hauptaugenmerk darauf, den Test besser lesbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-208">While it may be possible to combine some steps and reduce the size of your test, the primary goal is to make the test as readable as possible.</span></span>

#### <a name="bad"></a><span data-ttu-id="60ee8-209">Nicht empfohlen:</span><span class="sxs-lookup"><span data-stu-id="60ee8-209">Bad:</span></span>

[!code-csharp[BeforeArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a><span data-ttu-id="60ee8-210">Empfohlen:</span><span class="sxs-lookup"><span data-stu-id="60ee8-210">Better:</span></span>

[!code-csharp[AfterArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a><span data-ttu-id="60ee8-211">Schreiben von minimal erfolgreichen Tests</span><span class="sxs-lookup"><span data-stu-id="60ee8-211">Write minimally passing tests</span></span>

<span data-ttu-id="60ee8-212">Die in einem Komponententest verwendete Eingabe soll so einfach wie möglich gehalten werden, damit das Verhalten, das Sie gerade testen, überprüft werden kann.</span><span class="sxs-lookup"><span data-stu-id="60ee8-212">The input to be used in a unit test should be the simplest possible in order to verify the behavior that you are currently testing.</span></span>

#### <a name="why"></a><span data-ttu-id="60ee8-213">Warum?</span><span class="sxs-lookup"><span data-stu-id="60ee8-213">Why?</span></span>

- <span data-ttu-id="60ee8-214">Tests funktionieren auch nach Änderungen an der Codebasis wahrscheinlicher weiter.</span><span class="sxs-lookup"><span data-stu-id="60ee8-214">Tests become more resilient to future changes in the codebase.</span></span>
- <span data-ttu-id="60ee8-215">Das Testverhalten steht im Vordergrund, nicht die Implementierung.</span><span class="sxs-lookup"><span data-stu-id="60ee8-215">Closer to testing behavior over implementation.</span></span>

<span data-ttu-id="60ee8-216">Es ist wahrscheinlicher, dass Tests, die mehr Informationen enthalten, als für das Bestehen erforderlich sind, Fehler verursachen. Dadurch kann die Absicht des Tests weniger eindeutig sein.</span><span class="sxs-lookup"><span data-stu-id="60ee8-216">Tests that include more information than required to pass the test have a higher chance of introducing errors into the test and can make the intent of the test less clear.</span></span> <span data-ttu-id="60ee8-217">Wenn Sie Tests schreiben, sollte das Verhalten im Vordergrund stehen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-217">When writing tests, you want to focus on the behavior.</span></span> <span data-ttu-id="60ee8-218">Die Festlegung von zusätzlichen Eigenschaften für Modelle oder die Verwendung von Werten, die nicht 0 (null) sind, wenn es nicht nötig ist, lenkt nur vom gewünschten Ergebnis ab.</span><span class="sxs-lookup"><span data-stu-id="60ee8-218">Setting extra properties on models or using non-zero values when not required, only detracts from what you are trying to prove.</span></span>

#### <a name="bad"></a><span data-ttu-id="60ee8-219">Nicht empfohlen:</span><span class="sxs-lookup"><span data-stu-id="60ee8-219">Bad:</span></span>

[!code-csharp[BeforeMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a><span data-ttu-id="60ee8-220">Empfohlen:</span><span class="sxs-lookup"><span data-stu-id="60ee8-220">Better:</span></span>

[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a><span data-ttu-id="60ee8-221">Vermeiden „magischer“ Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="60ee8-221">Avoid magic strings</span></span>

<span data-ttu-id="60ee8-222">Das Benennen von Variablen in Komponententests ist genauso wichtig, wenn nicht noch wichtiger, wie das Benennen von Variablen im Produktionscode.</span><span class="sxs-lookup"><span data-stu-id="60ee8-222">Naming variables in unit tests is as important, if not more important, than naming variables in production code.</span></span> <span data-ttu-id="60ee8-223">Komponententests sollten keine „magischen“ Zeichenfolgen enthalten.</span><span class="sxs-lookup"><span data-stu-id="60ee8-223">Unit tests should not contain magic strings.</span></span>

#### <a name="why"></a><span data-ttu-id="60ee8-224">Warum?</span><span class="sxs-lookup"><span data-stu-id="60ee8-224">Why?</span></span>

- <span data-ttu-id="60ee8-225">Durch magische Zeichenfolgen sieht es der Leser des Tests womöglich nicht als notwendig an, den Produktionscode zu überprüfen, um herauszufinden, was den Wert besonders macht.</span><span class="sxs-lookup"><span data-stu-id="60ee8-225">Prevents the need for the reader of the test to inspect the production code in order to figure out what makes the value special.</span></span>
- <span data-ttu-id="60ee8-226">Sie stellen explizit dar, was Sie *beweisen* möchten und nicht, was Sie versuchen zu *erreichen*.</span><span class="sxs-lookup"><span data-stu-id="60ee8-226">Explicitly shows what you're trying to *prove* rather than trying to *accomplish*.</span></span>

<span data-ttu-id="60ee8-227">Magische Zeichenfolgen können den Leser Ihrer Tests verwirren.</span><span class="sxs-lookup"><span data-stu-id="60ee8-227">Magic strings can cause confusion to the reader of your tests.</span></span> <span data-ttu-id="60ee8-228">Wenn eine Zeichenfolge nicht wie gewohnt aussieht, fragt sich der Leser womöglich, warum ein bestimmter Wert für einen Parameter oder Rückgabewert ausgewählt wurde.</span><span class="sxs-lookup"><span data-stu-id="60ee8-228">If a string looks out of the ordinary, they may wonder why a certain value was chosen for a parameter or return value.</span></span> <span data-ttu-id="60ee8-229">Dadurch sieht sich der Leser möglicherweise die Implementierungsdetails genauer an und konzentriert sich so nicht mehr auf den Test.</span><span class="sxs-lookup"><span data-stu-id="60ee8-229">This may lead them to take a closer look at the implementation details, rather than focus on the test.</span></span>

> [!TIP]
> <span data-ttu-id="60ee8-230">Gehen Sie deshalb so genau wie möglich auf die Absicht ein, wenn Sie Tests schreiben.</span><span class="sxs-lookup"><span data-stu-id="60ee8-230">When writing tests, you should aim to express as much intent as possible.</span></span> <span data-ttu-id="60ee8-231">Im Fall von magischen Zeichenfolgen ist es ein guter Ansatz, diese Werte Kontanten zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-231">In the case of magic strings, a good approach is to assign these values to constants.</span></span>

#### <a name="bad"></a><span data-ttu-id="60ee8-232">Nicht empfohlen:</span><span class="sxs-lookup"><span data-stu-id="60ee8-232">Bad:</span></span>

[!code-csharp[BeforeMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a><span data-ttu-id="60ee8-233">Empfohlen:</span><span class="sxs-lookup"><span data-stu-id="60ee8-233">Better:</span></span>

[!code-csharp[AfterMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a><span data-ttu-id="60ee8-234">Vermeiden von Logik in Tests</span><span class="sxs-lookup"><span data-stu-id="60ee8-234">Avoid logic in tests</span></span>

<span data-ttu-id="60ee8-235">Wenn Sie Ihre Komponententests schreiben, vermeiden Sie manuelle Zeichenfolgenverkettungen und logische Bedingungen, z.B. `if`, `while`, `for`, `switch` usw.</span><span class="sxs-lookup"><span data-stu-id="60ee8-235">When writing your unit tests avoid manual string concatenation and logical conditions such as `if`, `while`, `for`, `switch`, etc.</span></span>

#### <a name="why"></a><span data-ttu-id="60ee8-236">Warum?</span><span class="sxs-lookup"><span data-stu-id="60ee8-236">Why?</span></span>

- <span data-ttu-id="60ee8-237">Es ist weniger wahrscheinlich, dass dies zu einem Fehler innerhalb Ihrer Tests führt.</span><span class="sxs-lookup"><span data-stu-id="60ee8-237">Less chance to introduce a bug inside of your tests.</span></span>
- <span data-ttu-id="60ee8-238">Konzentrieren Sie sich auf das Endergebnis und weniger auf die Implementierungsdetails.</span><span class="sxs-lookup"><span data-stu-id="60ee8-238">Focus on the end result, rather than implementation details.</span></span>

<span data-ttu-id="60ee8-239">Wenn Sie Logik in Ihre Testsammlung einfügen, erhöht sich die Wahrscheinlichkeit, dass dies zu einem Fehler führt.</span><span class="sxs-lookup"><span data-stu-id="60ee8-239">When you introduce logic into your test suite, the chance of introducing a bug into it increases dramatically.</span></span> <span data-ttu-id="60ee8-240">Ihre Testsammlung sollte auf keinen Fall einen Fehler enthalten.</span><span class="sxs-lookup"><span data-stu-id="60ee8-240">The last place that you want to find a bug is within your test suite.</span></span> <span data-ttu-id="60ee8-241">Sie müssen sich wirklich sicher sein, dass Ihre Tests funktionieren, andernfalls können Sie sich nicht auf diese verlassen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-241">You should have a high level of confidence that your tests work, otherwise, you will not trust them.</span></span> <span data-ttu-id="60ee8-242">Tests, auf die sie sich nicht verlassen können, haben keinen Nutzen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-242">Tests that you do not trust, do not provide any value.</span></span> <span data-ttu-id="60ee8-243">Wenn ein Test fehlschlägt, sollten Sie merken, dass etwas mit Ihrem Code tatsächlich nicht stimmt, und dass dies nicht ignoriert werden kann.</span><span class="sxs-lookup"><span data-stu-id="60ee8-243">When a test fails, you want to have a sense that something is actually wrong with your code and that it cannot be ignored.</span></span>

> [!TIP]
> <span data-ttu-id="60ee8-244">Wenn Logik in Ihrem Test unvermeidlich scheint, dann erwägen Sie, den Test in zwei oder mehr Tests aufzuteilen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-244">If logic in your test seems unavoidable, consider splitting the test up into two or more different tests.</span></span>

#### <a name="bad"></a><span data-ttu-id="60ee8-245">Nicht empfohlen:</span><span class="sxs-lookup"><span data-stu-id="60ee8-245">Bad:</span></span>

[!code-csharp[LogicInTests](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a><span data-ttu-id="60ee8-246">Empfohlen:</span><span class="sxs-lookup"><span data-stu-id="60ee8-246">Better:</span></span>

[!code-csharp[AfterTestLogic](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a><span data-ttu-id="60ee8-247">Hilfsmethoden statt SetUp und TearDown</span><span class="sxs-lookup"><span data-stu-id="60ee8-247">Prefer helper methods to setup and teardown</span></span>

<span data-ttu-id="60ee8-248">Wenn Sie für Ihre Test ein ähnliches Objekt oder einen ähnlichen Zustand benötigen, nutzen Sie anstatt der „Setup“- und „Teardown“-Attribute (falls vorhanden) lieber eine Hilfsmethode.</span><span class="sxs-lookup"><span data-stu-id="60ee8-248">If you require a similar object or state for your tests, prefer a helper method than leveraging Setup and Teardown attributes if they exist.</span></span>

#### <a name="why"></a><span data-ttu-id="60ee8-249">Warum?</span><span class="sxs-lookup"><span data-stu-id="60ee8-249">Why?</span></span>

- <span data-ttu-id="60ee8-250">Weniger Verwirrung beim Lesen der Tests, da der gesamte Code innerhalb der einzelnen Tests sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="60ee8-250">Less confusion when reading the tests since all of the code is visible from within each test.</span></span>
- <span data-ttu-id="60ee8-251">Für den spezifischen Test ist das Risiko geringer, zu viel oder zu wenig einzurichten.</span><span class="sxs-lookup"><span data-stu-id="60ee8-251">Less chance of setting up too much or too little for the given test.</span></span>
- <span data-ttu-id="60ee8-252">Geringeres Risiko, den Zustand zwischen Tests freizugeben, was zu unnötigen Abhängigkeiten zwischen diesen führen würde.</span><span class="sxs-lookup"><span data-stu-id="60ee8-252">Less chance of sharing state between tests, which creates unwanted dependencies between them.</span></span>

<span data-ttu-id="60ee8-253">In Komponententestframeworks wird `Setup` vor jedem Komponententest innerhalb Ihrer Testsammlung aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-253">In unit testing frameworks, `Setup` is called before each and every unit test within your test suite.</span></span> <span data-ttu-id="60ee8-254">Während einige diese Methode als nützlich betrachten, führt sie letztendlich doch zu überfrachteten und schwer zu lesenden Tests.</span><span class="sxs-lookup"><span data-stu-id="60ee8-254">While some may see this as a useful tool, it generally ends up leading to bloated and hard to read tests.</span></span> <span data-ttu-id="60ee8-255">Jeder Test hat in der Regel unterschiedliche Anforderungen, damit er ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="60ee8-255">Each test will generally have different requirements in order to get the test up and running.</span></span> <span data-ttu-id="60ee8-256">Leider werden Sie mit `Setup` gezwungen, exakt dieselben Anforderungen für jeden Test zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="60ee8-256">Unfortunately, `Setup` forces you to use the exact same requirements for each test.</span></span>

> [!NOTE]
> <span data-ttu-id="60ee8-257">Ab xUnit Version 2.x sind SetUp und TearDown nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="60ee8-257">xUnit has removed both SetUp and TearDown as of version 2.x</span></span>

#### <a name="bad"></a><span data-ttu-id="60ee8-258">Nicht empfohlen:</span><span class="sxs-lookup"><span data-stu-id="60ee8-258">Bad:</span></span>

[!code-csharp[BeforeSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a><span data-ttu-id="60ee8-259">Empfohlen:</span><span class="sxs-lookup"><span data-stu-id="60ee8-259">Better:</span></span>

[!code-csharp[AfterHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a><span data-ttu-id="60ee8-260">Vermeiden mehrerer Assert-Anweisungen</span><span class="sxs-lookup"><span data-stu-id="60ee8-260">Avoid multiple asserts</span></span>

<span data-ttu-id="60ee8-261">Wenn Sie Ihre Tests schreiben, versuchen Sie, nur eine Assert-Anweisung pro Test einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-261">When writing your tests, try to only include one Assert per test.</span></span> <span data-ttu-id="60ee8-262">Allgemeine Ansätze zur Verwendung von nur einer Assert-Anweisung sind die folgenden:</span><span class="sxs-lookup"><span data-stu-id="60ee8-262">Common approaches to using only one assert include:</span></span>

- <span data-ttu-id="60ee8-263">Erstellen eines separaten Tests für jede Assert-Anweisung</span><span class="sxs-lookup"><span data-stu-id="60ee8-263">Create a separate test for each assert.</span></span>
- <span data-ttu-id="60ee8-264">Verwenden parametrisierter Tests</span><span class="sxs-lookup"><span data-stu-id="60ee8-264">Use parameterized tests.</span></span>

#### <a name="why"></a><span data-ttu-id="60ee8-265">Warum?</span><span class="sxs-lookup"><span data-stu-id="60ee8-265">Why?</span></span>

- <span data-ttu-id="60ee8-266">Wenn eine Assert-Anweisung fehlschlägt, werden die darauffolgenden Assert-Vorgänge nicht ausgewertet.</span><span class="sxs-lookup"><span data-stu-id="60ee8-266">If one Assert fails, the subsequent Asserts will not be evaluated.</span></span>
- <span data-ttu-id="60ee8-267">Es wird sichergestellt, dass Sie nicht mehrere Fälle in Ihren Tests überprüfen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-267">Ensures you are not asserting multiple cases in your tests.</span></span>
- <span data-ttu-id="60ee8-268">Sie erhalten einen Überblick, warum Ihre Tests fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-268">Gives you the entire picture as to why your tests are failing.</span></span>

<span data-ttu-id="60ee8-269">Wenn mehrere Assert-Anweisungen in einer Testsituation verwendet werden, kann nicht garantiert werden, dass alle Assert-Anweisungen ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="60ee8-269">When introducing multiple asserts into a test case, it is not guaranteed that all of the asserts will be executed.</span></span> <span data-ttu-id="60ee8-270">In den meisten Komponententestframeworks wird automatisch angenommen, dass die nachfolgenden Tests fehlschlagen, sobald eine Überprüfung in einem Komponententest fehlschlägt.</span><span class="sxs-lookup"><span data-stu-id="60ee8-270">In most unit testing frameworks, once an assertion fails in a unit test, the proceeding tests are automatically considered to be failing.</span></span> <span data-ttu-id="60ee8-271">Dies kann verwirrend sein, da eine Funktion, die eigentlich funktioniert, als fehlgeschlagen angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="60ee8-271">This can be confusing as functionality that is actually working, will be shown as failing.</span></span>

> [!NOTE]
> <span data-ttu-id="60ee8-272">Eine Ausnahme bestätigt die Regel: das Überprüfen eines Objekts</span><span class="sxs-lookup"><span data-stu-id="60ee8-272">A common exception to this rule is when asserting against an object.</span></span> <span data-ttu-id="60ee8-273">In diesem Fall sind mehrere Assert-Anweisungen für jede Eigenschaft kein Problem, denn damit wird sichergestellt, dass sich das Objekt in dem Zustand befindet, den Sie von ihm erwarten.</span><span class="sxs-lookup"><span data-stu-id="60ee8-273">In this case, it is generally acceptable to have multiple asserts against each property to ensure the object is in the state that you expect it to be in.</span></span>

#### <a name="bad"></a><span data-ttu-id="60ee8-274">Nicht empfohlen:</span><span class="sxs-lookup"><span data-stu-id="60ee8-274">Bad:</span></span>

[!code-csharp[BeforeMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a><span data-ttu-id="60ee8-275">Empfohlen:</span><span class="sxs-lookup"><span data-stu-id="60ee8-275">Better:</span></span>

[!code-csharp[AfterMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a><span data-ttu-id="60ee8-276">Überprüfen privater Methoden durch Komponententest von öffentlichen Methoden</span><span class="sxs-lookup"><span data-stu-id="60ee8-276">Validate private methods by unit testing public methods</span></span>

<span data-ttu-id="60ee8-277">In den meisten Fällen sollte es nicht nötig sein, eine private Methode zu testen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-277">In most cases, there should not be a need to test a private method.</span></span> <span data-ttu-id="60ee8-278">Private Methoden sind ein Implementierungsdetail.</span><span class="sxs-lookup"><span data-stu-id="60ee8-278">Private methods are an implementation detail.</span></span> <span data-ttu-id="60ee8-279">Sie können sich diese wie folgt vorstellen: Private Methoden sind nie isoliert vorhanden.</span><span class="sxs-lookup"><span data-stu-id="60ee8-279">You can think of it this way: private methods never exist in isolation.</span></span> <span data-ttu-id="60ee8-280">Irgendwann wird eine öffentliche Methode die private Methode als Teil ihrer Implementierung aufrufen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-280">At some point, there is going to be a public facing method that calls the private method as part of its implementation.</span></span> <span data-ttu-id="60ee8-281">Sie sollten sich über das Endergebnis der öffentlichen Methode Gedanken machen, die die private abruft.</span><span class="sxs-lookup"><span data-stu-id="60ee8-281">What you should care about is the end result of the public method that calls into the private one.</span></span>

<span data-ttu-id="60ee8-282">Betrachten Sie folgenden Fall:</span><span class="sxs-lookup"><span data-stu-id="60ee8-282">Consider the following case</span></span>

```csharp
public string ParseLogLine(string input)
{
    var sanitizedInput = TrimInput(input);
    return sanitizedInput;
}

private string TrimInput(string input)
{
    return input.Trim();
}
```

<span data-ttu-id="60ee8-283">Möglicherweise versuchen Sie zunächst, einen Test für `TrimInput` zu schreiben, da Sie sicherstellen möchten, dass die Methode wie erwartet funktioniert.</span><span class="sxs-lookup"><span data-stu-id="60ee8-283">Your first reaction may be to start writing a test for `TrimInput` because you want to make sure that the method is working as expected.</span></span> <span data-ttu-id="60ee8-284">Es ist jedoch auch möglich, dass `sanitizedInput` von `ParseLogLine` auf unerwartete Weise manipuliert wird, wodurch das Rendern eines Tests für `TrimInput` nutzlos ist.</span><span class="sxs-lookup"><span data-stu-id="60ee8-284">However, it is entirely possible that `ParseLogLine` manipulates `sanitizedInput` in such a way that you do not expect, rendering a test against `TrimInput` useless.</span></span>

<span data-ttu-id="60ee8-285">Der echte Test sollte für die öffentliche Methode, `ParseLogLine`, ausgeführt werden, denn darum sollten Sie sich letztendlich kümmern.</span><span class="sxs-lookup"><span data-stu-id="60ee8-285">The real test should be done against the public facing method `ParseLogLine` because that is what you should ultimately care about.</span></span>

```csharp
public void ParseLogLine_StartsAndEndsWithSpace_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

<span data-ttu-id="60ee8-286">Wenn Sie mit diesem Wissen eine private Methode erkennen, suchen Sie nach der öffentlichen Methode, und schreiben Sie Ihre Tests für diese.</span><span class="sxs-lookup"><span data-stu-id="60ee8-286">With this viewpoint, if you see a private method, find the public method and write your tests against that method.</span></span> <span data-ttu-id="60ee8-287">Nur weil eine private Methode die erwarteten Ergebnisse liefert, bedeutet das nicht, dass das System, das letztendlich die private Methode aufruft, das Ergebnis richtig verwendet.</span><span class="sxs-lookup"><span data-stu-id="60ee8-287">Just because a private method returns the expected result, does not mean the system that eventually calls the private method uses the result correctly.</span></span>

### <a name="stub-static-references"></a><span data-ttu-id="60ee8-288">Statische Verweise für Stub</span><span class="sxs-lookup"><span data-stu-id="60ee8-288">Stub static references</span></span>

<span data-ttu-id="60ee8-289">Ein Komponententest muss das zu testende System vollständig steuern können.</span><span class="sxs-lookup"><span data-stu-id="60ee8-289">One of the principles of a unit test is that it must have full control of the system under test.</span></span> <span data-ttu-id="60ee8-290">Wenn der Produktionscode Aufrufe von statischen Verweisen (z.B. `DateTime.Now`) enthält, kann dies zu Problemen führen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-290">This can be problematic when production code includes calls to static references (for example, `DateTime.Now`).</span></span> <span data-ttu-id="60ee8-291">Betrachten Sie folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="60ee8-291">Consider the following code</span></span>

```csharp
public int GetDiscountedPrice(int price)
{
    if (DateTime.Now.DayOfWeek == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

<span data-ttu-id="60ee8-292">Wie kann für diesen Code am besten ein Komponententest ausgeführt werden?</span><span class="sxs-lookup"><span data-stu-id="60ee8-292">How can this code possibly be unit tested?</span></span> <span data-ttu-id="60ee8-293">Sie können beispielsweise folgenden Ansatz ausprobieren:</span><span class="sxs-lookup"><span data-stu-id="60ee8-293">You may try an approach such as</span></span>

```csharp
public void GetDiscountedPrice_NotTuesday_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(2, actual)
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(1, actual);
}
```

<span data-ttu-id="60ee8-294">Sie werden wahrscheinlich schnell merken, dass mit Ihren Tests leider einiges nicht stimmt.</span><span class="sxs-lookup"><span data-stu-id="60ee8-294">Unfortunately, you will quickly realize that there are a couple problems with your tests.</span></span>

- <span data-ttu-id="60ee8-295">Wenn die Testsammlung an einem Dienstag ausgeführt wird, ist der zweite Test erfolgreich, der erste schlägt jedoch fehl.</span><span class="sxs-lookup"><span data-stu-id="60ee8-295">If the test suite is run on a Tuesday, the second test will pass, but the first test will fail.</span></span>
- <span data-ttu-id="60ee8-296">Wenn die Testsammlung an einem anderen Tag ausgeführt wird, ist der erste Test erfolgreich, der zweite schlägt jedoch fehl.</span><span class="sxs-lookup"><span data-stu-id="60ee8-296">If the test suite is run on any other day, the first test will pass, but the second test will fail.</span></span>

<span data-ttu-id="60ee8-297">Sie müssen zur Lösung dieser Probleme eine *Nahtstelle* in Ihren Produktionscode einfügen.</span><span class="sxs-lookup"><span data-stu-id="60ee8-297">To solve these problems, you'll need to introduce a *seam* into your production code.</span></span> <span data-ttu-id="60ee8-298">Eine Methode ist das Umschließen des zu steuernden Codes mit einer Schnittstelle. Der Produktionscode soll dann von dieser Schnittstelle abhängig sein.</span><span class="sxs-lookup"><span data-stu-id="60ee8-298">One approach is to wrap the code that you need to control in an interface and have the production code depend on that interface.</span></span>

```csharp
public interface IDateTimeProvider
{
    DayOfWeek DayOfWeek();
}

public int GetDiscountedPrice(int price, IDateTimeProvider dateTimeProvider)
{
    if (dateTimeProvider.DayOfWeek() == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

<span data-ttu-id="60ee8-299">Ihre Testsammlung sieht nun so aus:</span><span class="sxs-lookup"><span data-stu-id="60ee8-299">Your test suite now becomes</span></span>

```csharp
public void GetDiscountedPrice_NotTuesday_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Monday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(2, actual);
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Tuesday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(1, actual);
}
```

<span data-ttu-id="60ee8-300">Die Testsammlung hat nun volle Kontrolle über `DateTime.Now` und kann für jeden Wert einen Stub ausführen, wenn die Methode aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="60ee8-300">Now the test suite has full control over `DateTime.Now` and can stub any value when calling into the method.</span></span>
