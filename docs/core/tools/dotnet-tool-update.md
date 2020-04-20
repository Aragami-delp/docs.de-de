---
title: Befehl „dotnet tool update“
description: Der Befehl „dotnet tool update“ aktualisiert das angegebene .NET Core-Tool auf Ihrem Computer.
ms.date: 02/14/2020
ms.openlocfilehash: 6176846dbe8e2a91d9c6959dede15718d8f983b2
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463302"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="f3dfe-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="f3dfe-103">dotnet tool update</span></span>

<span data-ttu-id="f3dfe-104">**Dieser Artikel gilt für:** ✔️ .NET Core 2.1 SDK und neuere Versionen</span><span class="sxs-lookup"><span data-stu-id="f3dfe-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f3dfe-105">name</span><span class="sxs-lookup"><span data-stu-id="f3dfe-105">Name</span></span>

<span data-ttu-id="f3dfe-106">`dotnet tool update`: Aktualisiert das angegebene [.NET Core-Tool](global-tools.md) auf Ihrem Computer.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-106">`dotnet tool update` - Updates the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f3dfe-107">Übersicht</span><span class="sxs-lookup"><span data-stu-id="f3dfe-107">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_NAME> -g|--global
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update <PACKAGE_NAME> --tool-path <PATH>
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update <PACKAGE_NAME>
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update -h|--help
```

## <a name="description"></a><span data-ttu-id="f3dfe-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f3dfe-108">Description</span></span>

<span data-ttu-id="f3dfe-109">Der Befehl `dotnet tool update` ermöglicht Ihnen das Aktualisieren der .NET Core-Tools auf Ihrem Computer auf die neueste stabile Version des Pakets.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-109">The `dotnet tool update` command provides a way for you to update .NET Core tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="f3dfe-110">Der Befehl deinstalliert und installiert ein Tool neu, sodass es aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-110">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="f3dfe-111">Um den Befehl zu verwenden, geben Sie eine der folgenden Optionen an:</span><span class="sxs-lookup"><span data-stu-id="f3dfe-111">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="f3dfe-112">Verwenden Sie zum Aktualisieren eines globalen Tools, das am Standardspeicherort installiert wurde, die Option `--global`.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-112">To update a global tool that was installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="f3dfe-113">Verwenden Sie zum Aktualisieren eines globalen Tools, das an einem benutzerdefinierten Speicherort installiert wurde, die Option `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-113">To update a global tool that was installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="f3dfe-114">Wenn Sie ein lokales Tool aktualisieren möchten, lassen Sie die Optionen `--global` und `--tool-path` weg.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-114">To update a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="f3dfe-115">**Lokale Tools sind ab .NET Core SDK 3.0 verfügbar.**</span><span class="sxs-lookup"><span data-stu-id="f3dfe-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="f3dfe-116">Argumente</span><span class="sxs-lookup"><span data-stu-id="f3dfe-116">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="f3dfe-117">Name oder ID des NuGet-Pakets, das das zu aktualisierende globale .NET Core-Tool enthält.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-117">Name/ID of the NuGet package that contains the .NET Core global tool to update.</span></span> <span data-ttu-id="f3dfe-118">Mithilfe des Befehls [dotnet tool list](dotnet-tool-list.md) können Sie den Paketnamen abrufen.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-118">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="f3dfe-119">Optionen</span><span class="sxs-lookup"><span data-stu-id="f3dfe-119">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="f3dfe-120">Fügt eine zusätzliche NuGet-Paketquelle für die Installation hinzu.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-120">Adds an additional NuGet package source to use during installation.</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="f3dfe-121">Die zu verwendende NuGet-Konfigurationsdatei (*nuget.config*).</span><span class="sxs-lookup"><span data-stu-id="f3dfe-121">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="f3dfe-122">Legt das [Zielframework](../../standard/frameworks.md) des zu aktualisierenden Tools fest.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-122">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

- **`-g|--global`**

  <span data-ttu-id="f3dfe-123">Gibt an, dass das Update für ein benutzerweites Tool ist.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-123">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="f3dfe-124">Kann nicht mit der Option `--tool-path` kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-124">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="f3dfe-125">Durch Weglassen von `--global` und `--tool-path` wird angegeben, dass das zu aktualisierende Tool ein lokales Tool ist.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-125">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f3dfe-126">Druckt eine kurze Hilfe für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-126">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="f3dfe-127">Gibt den Speicherort an, in dem das globale Tool installiert ist.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-127">Specifies the location where the global tool is installed.</span></span> <span data-ttu-id="f3dfe-128">„PATH“ kann absolut oder relativ sein.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-128">PATH can be absolute or relative.</span></span> <span data-ttu-id="f3dfe-129">Kann nicht mit der Option `--global` kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="f3dfe-130">Durch Weglassen von `--global` und `--tool-path` wird angegeben, dass das zu aktualisierende Tool ein lokales Tool ist.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-130">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f3dfe-131">Legt den Ausführlichkeitsgrad für den Befehl fest.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f3dfe-132">Zulässige Werte sind `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` und `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="f3dfe-133">Beispiele</span><span class="sxs-lookup"><span data-stu-id="f3dfe-133">Examples</span></span>

- **`dotnet tool update -g dotnetsay`**

  <span data-ttu-id="f3dfe-134">Aktualisiert das globale Tool [dotnetsay](https://www.nuget.org/packages/dotnetsay/).</span><span class="sxs-lookup"><span data-stu-id="f3dfe-134">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="f3dfe-135">Aktualisiert das globale Tool [dotnetsay](https://www.nuget.org/packages/dotnetsay/), das sich in einem bestimmten Windows-Verzeichnis befindet.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-135">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Windows directory.</span></span>

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="f3dfe-136">Aktualisiert das globale Tool [dotnetsay](https://www.nuget.org/packages/dotnetsay/), das sich in einem bestimmten Linux-/macOS-Verzeichnis befindet.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-136">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Linux/macOS directory.</span></span>

- **`dotnet tool update dotnetsay`**

  <span data-ttu-id="f3dfe-137">Aktualisiert das lokale Tool [dotnetsay](https://www.nuget.org/packages/dotnetsay/), das im lokalen Verzeichnis installiert ist.</span><span class="sxs-lookup"><span data-stu-id="f3dfe-137">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool installed for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3dfe-138">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f3dfe-138">See also</span></span>

- [<span data-ttu-id="f3dfe-139">.NET Core-Tools</span><span class="sxs-lookup"><span data-stu-id="f3dfe-139">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="f3dfe-140">Tutorial: Erstellen und Verwenden eines globalen .NET Core-Tools mithilfe der .NET Core-CLI</span><span class="sxs-lookup"><span data-stu-id="f3dfe-140">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="f3dfe-141">Tutorial: Erstellen und Verwenden eines lokalen .NET Core-Tools mithilfe der .NET Core-CLI</span><span class="sxs-lookup"><span data-stu-id="f3dfe-141">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
