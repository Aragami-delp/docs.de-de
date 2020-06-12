---
title: Organisieren und Testen von Projekten mit der .NET Core-CLI
description: In diesem Tutorial wird das Organisieren und Testen von .NET Core-Projekten von der Befehlszeile aus erläutert.
author: cartermp
ms.date: 09/10/2018
ms.openlocfilehash: 58c78c0f11ab1b275e4e4d05bf1da32562333c91
ms.sourcegitcommit: 0a798a7e9680e2d0a5a81a3eaa203870ea782883
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/03/2020
ms.locfileid: "84325944"
---
# <a name="organizing-and-testing-projects-with-the-net-core-cli"></a><span data-ttu-id="01c4f-103">Organisieren und Testen von Projekten mit der .NET Core-CLI</span><span class="sxs-lookup"><span data-stu-id="01c4f-103">Organizing and testing projects with the .NET Core CLI</span></span>

<span data-ttu-id="01c4f-104">Dieses Tutorial folgt auf das [Tutorial: Erstellen einer Konsolenanwendung mit .NET Core mithilfe von Visual Studio Code](with-visual-studio-code.md). Es geht über die Erstellung einer einfachen Konsolen-App hinaus und behandelt die Entwicklung komplexer und gut strukturierter Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="01c4f-104">This tutorial follows [Tutorial: Create a console application with .NET Core using Visual Studio Code](with-visual-studio-code.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="01c4f-105">Nachdem Sie gesehen haben, wie Sie Ordner zum Organisieren Ihres Codes verwenden können, zeigt Ihnen dieses Tutorial, wie Sie eine Konsolenanwendung mit dem [xUnit](https://xunit.github.io/)-Testframework erweitern können.</span><span class="sxs-lookup"><span data-stu-id="01c4f-105">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.github.io/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="01c4f-106">Verwenden von Ordnern zum Strukturieren von Code</span><span class="sxs-lookup"><span data-stu-id="01c4f-106">Using folders to organize code</span></span>

<span data-ttu-id="01c4f-107">Wenn Sie neue Typen in eine Konsolen-App einführen möchten, können Sie dies durch Hinzufügen von Dateien tun, die die Typen dieser App enthalten.</span><span class="sxs-lookup"><span data-stu-id="01c4f-107">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="01c4f-108">Wenn Sie Ihrem Projekt beispielsweise Dateien hinzufügen, die die Typen `AccountInformation` und `MonthlyReportRecords` enthalten, ist die Dateistruktur des Projekts flach und einfach zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="01c4f-108">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="01c4f-109">Dies funktioniert jedoch nur einwandfrei, wenn Ihr Projekt relativ klein ist.</span><span class="sxs-lookup"><span data-stu-id="01c4f-109">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="01c4f-110">Können Sie sich vorstellen, was passieren wird, wenn Sie 20 Typen zum Projekt hinzufügen?</span><span class="sxs-lookup"><span data-stu-id="01c4f-110">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="01c4f-111">Das Projekt wäre auf jeden Fall schwierig zu navigieren und zu warten, außerdem würden viele Dateien das Stammverzeichnis des Projekts unübersichtlich machen.</span><span class="sxs-lookup"><span data-stu-id="01c4f-111">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="01c4f-112">Um das Projekt zu organisieren, erstellen Sie einen neuen Ordner und nennen Ihn *Modelle*, der die Typdateien enthalten soll.</span><span class="sxs-lookup"><span data-stu-id="01c4f-112">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="01c4f-113">Platzieren Sie die Typdateien in den Ordner *Modelle*.</span><span class="sxs-lookup"><span data-stu-id="01c4f-113">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="01c4f-114">Projekte, die Dateien logisch in Ordner gruppieren, sind einfach zu navigieren und zu warten.</span><span class="sxs-lookup"><span data-stu-id="01c4f-114">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="01c4f-115">Im nächsten Abschnitt erstellen Sie ein komplexeres Beispiel mit Ordnern und Komponententests.</span><span class="sxs-lookup"><span data-stu-id="01c4f-115">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="01c4f-116">Organisieren und Testen mithilfe des NewTypes Pets-Beispiels</span><span class="sxs-lookup"><span data-stu-id="01c4f-116">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="01c4f-117">Erstellen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="01c4f-117">Building the sample</span></span>

<span data-ttu-id="01c4f-118">Sie können für die folgenden Schritte entweder mithilfe des [NewTypes Pets-Beispiels](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) durchführen oder Ihre eigenen Dateien und Ordner erstellen.</span><span class="sxs-lookup"><span data-stu-id="01c4f-118">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="01c4f-119">Die Typen werden logisch in einer Ordnerstruktur organisiert, die das spätere Hinzufügen zusätzlicher Typen erlaubt. Tests werden ebenso logisch in Ordnern platziert, wobei später weitere Tests durchgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="01c4f-119">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="01c4f-120">In diesem Beispiel sind zwei Typen enthalten, `Dog` und `Cat`, mit deren Hilfe die allgemeine Schnittstelle `IPet` implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="01c4f-120">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="01c4f-121">Ihr Ziel für das `NewTypes`-Projekt ist es, die auf Haustiere (pets) bezogenen Typen in einem *Pets*-Ordner zu organisieren.</span><span class="sxs-lookup"><span data-stu-id="01c4f-121">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="01c4f-122">Wenn andere Typen später hinzugefügt werden, z.B. *WildAnimals*, werden sie im *NewTypes*-Ordner neben dem *Pets*-Ordner platziert.</span><span class="sxs-lookup"><span data-stu-id="01c4f-122">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="01c4f-123">Der *WildAnimals*-Ordner kann womöglich Tierarten enthalten, die keine Haustiere sind, z.B. die Typen `Squirrel` und `Rabbit`.</span><span class="sxs-lookup"><span data-stu-id="01c4f-123">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="01c4f-124">Dadurch, dass Typen hinzugefügt werden, bleibt das Projekt organisiert.</span><span class="sxs-lookup"><span data-stu-id="01c4f-124">In this way as types are added, the project remains well organized.</span></span>

<span data-ttu-id="01c4f-125">Erstellen Sie die folgende Ordnerstruktur mit angegebenem Dateiinhalt:</span><span class="sxs-lookup"><span data-stu-id="01c4f-125">Create the following folder structure with file content indicated:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
```

<span data-ttu-id="01c4f-126">*IPet.cs*:</span><span class="sxs-lookup"><span data-stu-id="01c4f-126">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="01c4f-127">*Dog.cs*:</span><span class="sxs-lookup"><span data-stu-id="01c4f-127">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="01c4f-128">*Cat.cs*:</span><span class="sxs-lookup"><span data-stu-id="01c4f-128">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="01c4f-129">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="01c4f-129">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Program.cs)]

<span data-ttu-id="01c4f-130">*NewTypes.csproj*:</span><span class="sxs-lookup"><span data-stu-id="01c4f-130">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="01c4f-131">Führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="01c4f-131">Execute the following command:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="01c4f-132">Achten Sie auf die folgende Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="01c4f-132">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="01c4f-133">Optionale Übung: Sie können einen neuen Tiertyp hinzufügen, z.B. `Bird`, indem Sie dieses Projekt erweitern.</span><span class="sxs-lookup"><span data-stu-id="01c4f-133">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="01c4f-134">Die `TalkToOwner`-Methode des Vogels soll einen `Tweet!` an den Besitzer geben.</span><span class="sxs-lookup"><span data-stu-id="01c4f-134">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="01c4f-135">Führen Sie die App erneut aus.</span><span class="sxs-lookup"><span data-stu-id="01c4f-135">Run the app again.</span></span> <span data-ttu-id="01c4f-136">Die Ausgabe wird `Tweet!` enthalten.</span><span class="sxs-lookup"><span data-stu-id="01c4f-136">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="01c4f-137">Testen der Beispielanwendung</span><span class="sxs-lookup"><span data-stu-id="01c4f-137">Testing the sample</span></span>

<span data-ttu-id="01c4f-138">Das `NewTypes`-Projekt ist platziert, und Sie haben es organisiert, indem Sie die auf Haustiere bezogenen Typen in einem Ordner gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="01c4f-138">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="01c4f-139">Erstellen Sie als Nächstes Ihr Testprojekt und beginnen Sie, Tests mit dem [xUnit](https://xunit.github.io/)-Testframework zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="01c4f-139">Next, create your test project and start writing tests with the [xUnit](https://xunit.github.io/) test framework.</span></span> <span data-ttu-id="01c4f-140">Komponententests erlauben Ihnen, das Verhalten dieser Typen automatisch zu testen, um zu überprüfen, ob sie ordnungsgemäß funktionieren.</span><span class="sxs-lookup"><span data-stu-id="01c4f-140">Unit testing allows you to automatically check the behavior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="01c4f-141">Navigieren Sie zurück zum Ordner *src*, und erstellen Sie einen Ordner *test*, der den Ordner *NewTypesTests* enthält.</span><span class="sxs-lookup"><span data-stu-id="01c4f-141">Navigate back to the *src* folder and create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="01c4f-142">Führen Sie in einer Eingabeaufforderung vom *NewTypesTests*-Ordner `dotnet new xunit` aus.</span><span class="sxs-lookup"><span data-stu-id="01c4f-142">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="01c4f-143">Dies ergibt zwei Dateien: *NewTypesTests.csproj* und *UnitTest1.cs*.</span><span class="sxs-lookup"><span data-stu-id="01c4f-143">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="01c4f-144">Das Testprojekt kann derzeit nicht die Typen in `NewTypes` testen und benötigt einen Projektverweis auf das `NewTypes`-Projekt.</span><span class="sxs-lookup"><span data-stu-id="01c4f-144">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="01c4f-145">Um einen Projektverweis hinzuzufügen, verwenden Sie den [`dotnet add reference`](../tools/dotnet-add-reference.md)-Befehl:</span><span class="sxs-lookup"><span data-stu-id="01c4f-145">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="01c4f-146">Alternativ haben Sie auch die Möglichkeit, den Projektverweis manuell hinzuzufügen, indem Sie der *NewTypesTests.csproj*-Datei einen `<ItemGroup>`-Knoten hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="01c4f-146">Or, you also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="01c4f-147">*NewTypesTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="01c4f-147">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="01c4f-148">Die *NewTypesTests.csproj*-Datei enthält Folgendes:</span><span class="sxs-lookup"><span data-stu-id="01c4f-148">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="01c4f-149">Paketverweis auf `Microsoft.NET.Test.Sdk`, die .NET-Testinfrastruktur</span><span class="sxs-lookup"><span data-stu-id="01c4f-149">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="01c4f-150">Paketverweis auf `xunit`, das xUnit-Testframework</span><span class="sxs-lookup"><span data-stu-id="01c4f-150">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="01c4f-151">Paketverweis auf `xunit.runner.visualstudio`, der Test Runner</span><span class="sxs-lookup"><span data-stu-id="01c4f-151">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="01c4f-152">Projektverweis auf `NewTypes`, der zu testende Code</span><span class="sxs-lookup"><span data-stu-id="01c4f-152">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="01c4f-153">Ändern Sie den Namen von *UnitTest1.cs* zu *PetTests.cs*, und ersetzen Sie den Code in der Datei mit Folgendem:</span><span class="sxs-lookup"><span data-stu-id="01c4f-153">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

```csharp
using System;
using Xunit;
using Pets;

public class PetTests
{
    [Fact]
    public void DogTalkToOwnerReturnsWoof()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();

        Assert.NotEqual(expected, actual);
    }

    [Fact]
    public void CatTalkToOwnerReturnsMeow()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();

        Assert.NotEqual(expected, actual);
    }
}
```

<span data-ttu-id="01c4f-154">Optionale Übung: Wenn Sie zuvor einen `Bird`-Typ hinzugefügt haben, der `Tweet!` dem Besitzer zurückgibt, fügen Sie der *PetTests.cs*-Datei eine Testmethode hinzu, `BirdTalkToOwnerReturnsTweet`, um zu überprüfen, ob die `TalkToOwner`-Methode für den `Bird`-Typ ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="01c4f-154">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="01c4f-155">Obwohl Sie erwarten, dass die Werte `expected` und `actual` gleich sind, gibt die anfängliche Assertion mit der `Assert.NotEqual`-Überprüfung an, dass sie *nicht gleich* sind.</span><span class="sxs-lookup"><span data-stu-id="01c4f-155">Although you expect that the `expected` and `actual` values are equal, an initial assertion with the `Assert.NotEqual` check specifies that these values are *not equal*.</span></span> <span data-ttu-id="01c4f-156">Erstellen Sie zunächst immer einen Test, damit dieser fehlschlagen und die Logik des Tests überprüft werden kann.</span><span class="sxs-lookup"><span data-stu-id="01c4f-156">Always initially create a test to fail in order to check the logic of the test.</span></span> <span data-ttu-id="01c4f-157">Nachdem Sie das Fehlschlagen des Tests bestätigt haben, können Sie die Assertion so anpassen, dass der Test erfolgreich verläuft.</span><span class="sxs-lookup"><span data-stu-id="01c4f-157">After you confirm that the test fails, adjust the assertion to allow the test to pass.</span></span>

<span data-ttu-id="01c4f-158">Nachstehend ist die vollständige Projektstruktur dargestellt:</span><span class="sxs-lookup"><span data-stu-id="01c4f-158">The following shows the complete project structure:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__NewTypesTests.csproj
```

<span data-ttu-id="01c4f-159">Beginnen Sie im *test/NewTypesTests*-Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="01c4f-159">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="01c4f-160">Stellen Sie das Testprojekt mit dem [`dotnet restore`](../tools/dotnet-restore.md)-Befehl wieder her.</span><span class="sxs-lookup"><span data-stu-id="01c4f-160">Restore the test project with the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="01c4f-161">Führen Sie die Tests mit dem [`dotnet test`](../tools/dotnet-test.md)-Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="01c4f-161">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="01c4f-162">Dieser Befehl startet den in der Projektdatei angegebenen Test Runner.</span><span class="sxs-lookup"><span data-stu-id="01c4f-162">This command starts the test runner specified in the project file.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="01c4f-163">Der Test schlägt wie erwartet fehl, und die Konsole zeigt die folgende Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="01c4f-163">As expected, testing fails, and the console displays the following output:</span></span>

```output
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:00.77]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
[xUnit.net 00:00:00.78]     PetTests.CatTalkToOwnerReturnsMeow [FAIL]
Failed   PetTests.DogTalkToOwnerReturnsWoof
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
Stack Trace:
   at PetTests.DogTalkToOwnerReturnsWoof() in c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 13
Failed   PetTests.CatTalkToOwnerReturnsMeow
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Meow!"
Actual:   "Meow!"
Stack Trace:
   at PetTests.CatTalkToOwnerReturnsMeow() in c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 22

Total tests: 2. Passed: 0. Failed: 2. Skipped: 0.
Test Run Failed.
Test execution time: 1.7000 Seconds
```

<span data-ttu-id="01c4f-164">Ändern Sie die Assertionen Ihrer Tests von `Assert.NotEqual` zu `Assert.Equal`:</span><span class="sxs-lookup"><span data-stu-id="01c4f-164">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="01c4f-165">Führen Sie die Tests erneut mit dem `dotnet test`-Befehl aus, und achten Sie auf die folgende Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="01c4f-165">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```output
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6029 Seconds
```

<span data-ttu-id="01c4f-166">Die Tests werden erfolgreich ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="01c4f-166">Testing passes.</span></span> <span data-ttu-id="01c4f-167">Die Haustiertyp-Methoden geben die korrekten Werte zurück, wenn sie mit dem Besitzer kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="01c4f-167">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="01c4f-168">Sie haben Techniken zum Organisieren und Testen von Projekten mithilfe von xUnit gelernt.</span><span class="sxs-lookup"><span data-stu-id="01c4f-168">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="01c4f-169">Machen Sie mit diesen Techniken weiter, und wenden Sie sie in Ihren eigenen Projekten an.</span><span class="sxs-lookup"><span data-stu-id="01c4f-169">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="01c4f-170">*Viel Spaß beim Programmieren!*</span><span class="sxs-lookup"><span data-stu-id="01c4f-170">*Happy coding!*</span></span>
