---
title: Komponententests in .NET Core und .NET Standard
description: Dieser Artikel bietet eine kurze Übersicht über Komponententests für .NET Core- und .NET Standard-Projekte.
author: ardalis
ms.author: wiwagn
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: e15f80b173389cdff86c6e62013e9c0f21171dd6
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703108"
---
# <a name="unit-testing-in-net-core-and-net-standard"></a><span data-ttu-id="b9c28-103">Komponententests in .NET Core und .NET Standard</span><span class="sxs-lookup"><span data-stu-id="b9c28-103">Unit testing in .NET Core and .NET Standard</span></span>

<span data-ttu-id="b9c28-104">Mit .NET Core können Sie im Handumdrehen Komponententests erstellen.</span><span class="sxs-lookup"><span data-stu-id="b9c28-104">.NET Core makes it easy to create unit tests.</span></span> <span data-ttu-id="b9c28-105">Dieser Artikel gibt eine kurze Einführung zu Komponententests (und wie sich diese von anderen Arten von Tests unterscheiden).</span><span class="sxs-lookup"><span data-stu-id="b9c28-105">This article introduces unit tests and illustrates how they differ from other kinds of tests.</span></span> <span data-ttu-id="b9c28-106">Über die am Ende der Seite verlinkten Ressourcen erfahren Sie, wie Sie einer Projektmappe ein neues Testprojekt hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b9c28-106">The linked resources near the bottom of the page show you how to add a test project to your solution.</span></span> <span data-ttu-id="b9c28-107">Nachdem Sie Ihre Testprojekte erstellt haben, können Sie Ihre Komponententests über die Befehlszeile oder Visual Studio durchführen.</span><span class="sxs-lookup"><span data-stu-id="b9c28-107">After you set up your test project, you will be able to run your unit tests using the command line or Visual Studio.</span></span>

<span data-ttu-id="b9c28-108">Wenn Sie ein **ASP.NET Core**-Projekt testen, finden Sie weitere Informationen unter [Integrationstests in ASP.NET Core](/aspnet/core/test/integration-tests#test-app-prerequisites).</span><span class="sxs-lookup"><span data-stu-id="b9c28-108">If you're testing an **ASP.NET Core** project, see [Integration tests in ASP.NET Core](/aspnet/core/test/integration-tests#test-app-prerequisites).</span></span>

<span data-ttu-id="b9c28-109">.NET Core 2.0 und höher unterstützt [.NET Standard 2.0](../../standard/net-standard.md). Wir verwenden die dazugehörigen Bibliotheken, um Komponententests zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="b9c28-109">.NET Core 2.0 and later supports [.NET Standard 2.0](../../standard/net-standard.md), and we will use its libraries to demonstrate unit tests.</span></span>

<span data-ttu-id="b9c28-110">Sie können in .NET Core 2.0 oder höher integrierte Vorlagen für Komponententestprojekte für C#, F# und Visual Basic als Ausgangspunkt für Ihr eigenes Projekt verwenden.</span><span class="sxs-lookup"><span data-stu-id="b9c28-110">You are able to use built-in .NET Core 2.0 and later unit test project templates for C#, F# and Visual Basic as a starting point for your personal project.</span></span>

## <a name="what-are-unit-tests"></a><span data-ttu-id="b9c28-111">Was sind Komponententests?</span><span class="sxs-lookup"><span data-stu-id="b9c28-111">What are unit tests?</span></span>

<span data-ttu-id="b9c28-112">Mit automatisierten Tests können Sie sicherstellen, dass eine Softwareanwendung das tut, was die Autoren möchten.</span><span class="sxs-lookup"><span data-stu-id="b9c28-112">Having automated tests is a great way to ensure a software application does what its authors intend it to do.</span></span> <span data-ttu-id="b9c28-113">Es gibt mehrere Arten von Tests für Softwareanwendungen.</span><span class="sxs-lookup"><span data-stu-id="b9c28-113">There are multiple types of tests for software applications.</span></span> <span data-ttu-id="b9c28-114">Dazu zählen u.a. Integrationstests, Webtests und Auslastungstests.</span><span class="sxs-lookup"><span data-stu-id="b9c28-114">These include integration tests, web tests, load tests, and others.</span></span> <span data-ttu-id="b9c28-115">**Komponententests** testen einzelne Softwarekomponenten und Methoden.</span><span class="sxs-lookup"><span data-stu-id="b9c28-115">**Unit tests** test individual software components and methods.</span></span> <span data-ttu-id="b9c28-116">Komponententests sollten nur den Code testen, für den der Entwickler zuständig ist.</span><span class="sxs-lookup"><span data-stu-id="b9c28-116">Unit tests should only test code within the developer’s control.</span></span> <span data-ttu-id="b9c28-117">Sie sollten keine Aspekte der Infrastruktur testen.</span><span class="sxs-lookup"><span data-stu-id="b9c28-117">They should not test infrastructure concerns.</span></span> <span data-ttu-id="b9c28-118">Aspekte der Infrastruktur sind z.B. Datenbanken, Dateisysteme und Netzwerkressourcen.</span><span class="sxs-lookup"><span data-stu-id="b9c28-118">Infrastructure concerns include databases, file systems, and network resources.</span></span>

<span data-ttu-id="b9c28-119">Beachten Sie, dass es bewährte Methode für das Schreiben von Tests gibt.</span><span class="sxs-lookup"><span data-stu-id="b9c28-119">Also, keep in mind there are best practices for writing tests.</span></span> <span data-ttu-id="b9c28-120">Bei der [testgesteuerten Entwicklung (Test Driven Development, TDD)](https://deviq.com/test-driven-development/) wird ein Komponententest vor dem Code geschrieben, den er prüfen soll.</span><span class="sxs-lookup"><span data-stu-id="b9c28-120">For example, [Test Driven Development (TDD)](https://deviq.com/test-driven-development/) is when a unit test is written before the code it is meant to check.</span></span> <span data-ttu-id="b9c28-121">Stellen Sie sich die TDD wie eine Gliederung für ein Buch vor, bevor dieses geschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="b9c28-121">TDD is like creating an outline for a book before we write it.</span></span> <span data-ttu-id="b9c28-122">Dadurch sollen Entwickler einfacheren, lesbareren und effizienteren Code schreiben können.</span><span class="sxs-lookup"><span data-stu-id="b9c28-122">It is meant to help developers write simpler, more readable, and efficient code.</span></span>

> [!NOTE]
> <span data-ttu-id="b9c28-123">Das ASP.NET-Team hält sich an [diese Konventionen](https://github.com/dotnet/aspnetcore/wiki/Engineering-guidelines#unit-tests-and-functional-tests), um Entwicklern das Festlegen von aussagekräftigen Namen für Testklassen und -methoden zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="b9c28-123">The ASP.NET team follows [these conventions](https://github.com/dotnet/aspnetcore/wiki/Engineering-guidelines#unit-tests-and-functional-tests) to help developers come up with good names for test classes and methods.</span></span>

<span data-ttu-id="b9c28-124">Achten Sie beim Schreiben von Komponententests darauf, dass diese nicht von der Infrastruktur abhängig sind.</span><span class="sxs-lookup"><span data-stu-id="b9c28-124">Try not to introduce dependencies on infrastructure when writing unit tests.</span></span> <span data-ttu-id="b9c28-125">Dadurch werden die Tests langsam und fehleranfällig. Diese Abhängigkeiten sollten nur bei Integrationstests bestehen.</span><span class="sxs-lookup"><span data-stu-id="b9c28-125">These make the tests slow and brittle, and should be reserved for integration tests.</span></span> <span data-ttu-id="b9c28-126">Sie können diese Abhängigkeiten in Ihrem Code vermeiden, indem Sie das [Prinzip der expliziten Abhängigkeit](https://deviq.com/explicit-dependencies-principle/) und [Dependency Injection](/aspnet/core/fundamentals/dependency-injection) einsetzen.</span><span class="sxs-lookup"><span data-stu-id="b9c28-126">You can avoid these dependencies in your application by following the [Explicit Dependencies Principle](https://deviq.com/explicit-dependencies-principle/) and using [Dependency Injection](/aspnet/core/fundamentals/dependency-injection).</span></span> <span data-ttu-id="b9c28-127">Sie können die Komponententests und die Integrationstests in unterschiedlichen Projekten erstellen.</span><span class="sxs-lookup"><span data-stu-id="b9c28-127">You can also keep your unit tests in a separate project from your integration tests.</span></span> <span data-ttu-id="b9c28-128">Dadurch wird sichergestellt, dass Ihr Komponententestprojekt keine Verweise auf oder Abhängigkeiten von Infrastrukturpaketen aufweist.</span><span class="sxs-lookup"><span data-stu-id="b9c28-128">This ensures your unit test project doesn’t have references to or dependencies on infrastructure packages.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b9c28-129">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="b9c28-129">Next steps</span></span>

<span data-ttu-id="b9c28-130">Mehr Informationen zu Unittests in .NET Core-Projekten:</span><span class="sxs-lookup"><span data-stu-id="b9c28-130">More information on unit testing in .NET Core projects:</span></span>

<span data-ttu-id="b9c28-131">.NET Core-Komponententestprojekte werden für folgende Programmiersprachen unterstützt:</span><span class="sxs-lookup"><span data-stu-id="b9c28-131">.NET Core unit test projects are supported for:</span></span>

- [<span data-ttu-id="b9c28-132">C#</span><span class="sxs-lookup"><span data-stu-id="b9c28-132">C#</span></span>](../../csharp/index.yml)
- [<span data-ttu-id="b9c28-133">F#</span><span class="sxs-lookup"><span data-stu-id="b9c28-133">F#</span></span>](../../fsharp/index.yml)
- [<span data-ttu-id="b9c28-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b9c28-134">Visual Basic</span></span>](../../visual-basic/index.yml)

<span data-ttu-id="b9c28-135">Sie können auch zwischen mehreren Komponententestframeworks auswählen:</span><span class="sxs-lookup"><span data-stu-id="b9c28-135">You can also choose between several unit test frameworks:</span></span>

- [<span data-ttu-id="b9c28-136">xUnit</span><span class="sxs-lookup"><span data-stu-id="b9c28-136">xUnit</span></span>](https://xunit.net/)
- [<span data-ttu-id="b9c28-137">NUnit</span><span class="sxs-lookup"><span data-stu-id="b9c28-137">NUnit</span></span>](https://nunit.org)
- [<span data-ttu-id="b9c28-138">MSTest</span><span class="sxs-lookup"><span data-stu-id="b9c28-138">MSTest</span></span>](https://github.com/Microsoft/testfx-docs)

<span data-ttu-id="b9c28-139">In den folgenden exemplarischen Vorgehensweisen erfahren Sie mehr:</span><span class="sxs-lookup"><span data-stu-id="b9c28-139">You can learn more in the following walkthroughs:</span></span>

:::zone pivot="mstest"

- <span data-ttu-id="b9c28-140">Erstellen von Komponententests mit [*MSTest* und *C#* mit der .NET Core-CLI](unit-testing-with-mstest.md).</span><span class="sxs-lookup"><span data-stu-id="b9c28-140">Create unit tests using [*MSTest* and *C#* with the .NET Core CLI](unit-testing-with-mstest.md).</span></span>
- <span data-ttu-id="b9c28-141">Erstellen von Komponententests mit [*MSTest* und *F#* mit der .NET Core-CLI](unit-testing-fsharp-with-mstest.md).</span><span class="sxs-lookup"><span data-stu-id="b9c28-141">Create unit tests using [*MSTest* and *F#* with the .NET Core CLI](unit-testing-fsharp-with-mstest.md).</span></span>
- <span data-ttu-id="b9c28-142">Erstellen von Komponententests mit [*MSTest* und *Visual Basic* mit der .NET Core-CLI](unit-testing-visual-basic-with-mstest.md).</span><span class="sxs-lookup"><span data-stu-id="b9c28-142">Create unit tests using [*MSTest* and *Visual Basic* with the .NET Core CLI](unit-testing-visual-basic-with-mstest.md).</span></span>

:::zone-end
:::zone pivot="xunit"

- <span data-ttu-id="b9c28-143">Erstellen von Komponententests mit [*xUnit* und *C#* mit der .NET Core-CLI](unit-testing-with-dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="b9c28-143">Create unit tests using [*xUnit* and *C#* with the .NET Core CLI](unit-testing-with-dotnet-test.md).</span></span>
- <span data-ttu-id="b9c28-144">Erstellen von Komponententests mit [*xUnit* und *F#* mit der .NET Core-CLI](unit-testing-fsharp-with-dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="b9c28-144">Create unit tests using [*xUnit* and *F#* with the .NET Core CLI](unit-testing-fsharp-with-dotnet-test.md).</span></span>
- <span data-ttu-id="b9c28-145">Erstellen von Komponententests mit [*xUnit* und *Visual Basic* mit der .NET Core-CLI](unit-testing-visual-basic-with-dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="b9c28-145">Create unit tests using [*xUnit* and *Visual Basic* with the .NET Core CLI](unit-testing-visual-basic-with-dotnet-test.md).</span></span>

:::zone-end
:::zone pivot="nunit"

- <span data-ttu-id="b9c28-146">Erstellen von Komponententests mit [*NUnit* und *C#* mit der .NET Core-CLI](unit-testing-with-nunit.md).</span><span class="sxs-lookup"><span data-stu-id="b9c28-146">Create unit tests using [*NUnit* and *C#* with the .NET Core CLI](unit-testing-with-nunit.md).</span></span>
- <span data-ttu-id="b9c28-147">Erstellen von Komponententests mit [*NUnit* und *F#* mit der .NET Core-CLI](unit-testing-fsharp-with-nunit.md).</span><span class="sxs-lookup"><span data-stu-id="b9c28-147">Create unit tests using [*NUnit* and *F#* with the .NET Core CLI](unit-testing-fsharp-with-nunit.md).</span></span>
- <span data-ttu-id="b9c28-148">Erstellen von Komponententests mit [*NUnit* und *Visual Basic* mit der .NET Core-CLI](unit-testing-visual-basic-with-nunit.md).</span><span class="sxs-lookup"><span data-stu-id="b9c28-148">Create unit tests using [*NUnit* and *Visual Basic* with the .NET Core CLI](unit-testing-visual-basic-with-nunit.md).</span></span>

:::zone-end

<span data-ttu-id="b9c28-149">In den folgenden Artikeln erfahren Sie mehr:</span><span class="sxs-lookup"><span data-stu-id="b9c28-149">You can learn more in the following articles:</span></span>

- <span data-ttu-id="b9c28-150">Visual Studio Enterprise bietet nützliche Testtools für .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b9c28-150">Visual Studio Enterprise offers great testing tools for .NET Core.</span></span> <span data-ttu-id="b9c28-151">Weitere Informationen finden Sie in den Artikel zu [Live Unit Testing](/visualstudio/test/live-unit-testing) und [Codeabdeckung](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage).</span><span class="sxs-lookup"><span data-stu-id="b9c28-151">Check out [Live Unit Testing](/visualstudio/test/live-unit-testing) or [code coverage](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage) to learn more.</span></span>
- <span data-ttu-id="b9c28-152">Weitere Informationen zum Durchführen selektiver Komponententests finden Sie unter [Ausführen von selektiven Komponententests](selective-unit-tests.md) und [Including and excluding test projects and test methods](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods) (Einbeziehen und Ausschließen von Testprojekten und Testmethoden).</span><span class="sxs-lookup"><span data-stu-id="b9c28-152">For more information on how to run selective unit tests, see [Running selective unit tests](selective-unit-tests.md), or [including and excluding tests with Visual Studio](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods).</span></span>
- <span data-ttu-id="b9c28-153">[Verwenden von XUnit mit .NET Core und Visual Studio](https://xunit.github.io/docs/getting-started-dotnet-core.html)</span><span class="sxs-lookup"><span data-stu-id="b9c28-153">[How to use xUnit with .NET Core and Visual Studio](https://xunit.github.io/docs/getting-started-dotnet-core.html).</span></span>
