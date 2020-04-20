---
title: dotnet store-befehl
description: Der „dotnet store“-Befehl speichert die angegebenen Assemblys im Laufzeitpaketspeicher.
ms.date: 02/14/2020
ms.openlocfilehash: 2f28a9bc287a87f600bda385c579e8070cbaa5ab
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463384"
---
# <a name="dotnet-store"></a><span data-ttu-id="5db6b-103">dotnet store</span><span class="sxs-lookup"><span data-stu-id="5db6b-103">dotnet store</span></span>

<span data-ttu-id="5db6b-104">**Dieser Artikel gilt für:** ✔️ .NET Core 2.x SDK und neuere Versionen</span><span class="sxs-lookup"><span data-stu-id="5db6b-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5db6b-105">Name</span><span class="sxs-lookup"><span data-stu-id="5db6b-105">Name</span></span>

<span data-ttu-id="5db6b-106">`dotnet store`: speichert die angegebenen Assemblys im [Laufzeitpaketspeicher](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="5db6b-106">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="5db6b-107">Übersicht</span><span class="sxs-lookup"><span data-stu-id="5db6b-107">Synopsis</span></span>

```dotnetcli
dotnet store -m|--manifest <PATH_TO_MANIFEST_FILE>
    -f|--framework <FRAMEWORK_VERSION> -r|--runtime <RUNTIME_IDENTIFIER>
    [--framework-version <FRAMEWORK_VERSION>] [--output <OUTPUT_DIRECTORY>]
    [--skip-optimization] [--skip-symbols] [-v|--verbosity <LEVEL>]
    [--working-dir <WORKING_DIRECTORY>]

dotnet store -h|--help
```

## <a name="description"></a><span data-ttu-id="5db6b-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5db6b-108">Description</span></span>

<span data-ttu-id="5db6b-109">`dotnet store`: speichert die angegebenen Assemblys im [Laufzeitpaketspeicher](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="5db6b-109">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="5db6b-110">Assemblys werden standardmäßig für die Ziellaufzeit und das Zielframework optimiert.</span><span class="sxs-lookup"><span data-stu-id="5db6b-110">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="5db6b-111">Weitere Informationen finden Sie unter [Laufzeitpaketspeicher](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="5db6b-111">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="5db6b-112">Erforderliche Optionen</span><span class="sxs-lookup"><span data-stu-id="5db6b-112">Required options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="5db6b-113">Gibt das [Zielframework](../../standard/frameworks.md) an.</span><span class="sxs-lookup"><span data-stu-id="5db6b-113">Specifies the [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="5db6b-114">Das Zielframework muss in der Projektdatei angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="5db6b-114">The target framework has to be specified in the project file.</span></span>

- **`-m|--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="5db6b-115">Die *Manifestdatei des Paketspeichers* ist eine XML-Datei, die die Liste der zu speichernden Pakete enthält.</span><span class="sxs-lookup"><span data-stu-id="5db6b-115">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="5db6b-116">Das Format der Manifestdatei ist mit dem SDK-Projektformat kompatibel.</span><span class="sxs-lookup"><span data-stu-id="5db6b-116">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="5db6b-117">Also kann eine Projektdatei, die auf das gewünschte Paket verweist, mit der Option `-m|--manifest` verwendet werden, um Assemblys im Laufzeitpaketspeicher zu speichern.</span><span class="sxs-lookup"><span data-stu-id="5db6b-117">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="5db6b-118">Wiederholen Sie die Option und den Pfad für jede Datei, um mehrere Manifestdateien anzugeben.</span><span class="sxs-lookup"><span data-stu-id="5db6b-118">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="5db6b-119">Beispiel: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="5db6b-119">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="5db6b-120">Der als Ziel zu verwendende [Laufzeitbezeichner](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="5db6b-120">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="5db6b-121">Optionale Optionen</span><span class="sxs-lookup"><span data-stu-id="5db6b-121">Optional options</span></span>

- **`--framework-version <FRAMEWORK_VERSION>`**

  <span data-ttu-id="5db6b-122">Gibt die Version des .NET Core SDK an.</span><span class="sxs-lookup"><span data-stu-id="5db6b-122">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="5db6b-123">Mit dieser Option können Sie eine bestimmte Frameworkversion auswählen, die nicht das von der `-f|--framework`-Option angegebene Framework ist.</span><span class="sxs-lookup"><span data-stu-id="5db6b-123">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

- **`-h|--help`**

  <span data-ttu-id="5db6b-124">Zeigt Hilfeinformationen</span><span class="sxs-lookup"><span data-stu-id="5db6b-124">Shows help information.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="5db6b-125">Gibt den Pfad zum Laufzeitpaketspeicher an.</span><span class="sxs-lookup"><span data-stu-id="5db6b-125">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="5db6b-126">Wenn nicht angegeben, wird das Unterverzeichnis *store* des .NET Core-Installationsverzeichnisses des Benutzerprofils als Standardeinstellung verwendet.</span><span class="sxs-lookup"><span data-stu-id="5db6b-126">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

- **`--skip-optimization`**

  <span data-ttu-id="5db6b-127">Überspringt die Optimierungsphase</span><span class="sxs-lookup"><span data-stu-id="5db6b-127">Skips the optimization phase.</span></span>

- **`--skip-symbols`**

  <span data-ttu-id="5db6b-128">Überspringt die Symbolgenerierung.</span><span class="sxs-lookup"><span data-stu-id="5db6b-128">Skips symbol generation.</span></span> <span data-ttu-id="5db6b-129">Sie können aktuell nur unter Windows und Linux Symbole generieren.</span><span class="sxs-lookup"><span data-stu-id="5db6b-129">Currently, you can only generate symbols on Windows and Linux.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="5db6b-130">Legt den Ausführlichkeitsgrad für den Befehl fest.</span><span class="sxs-lookup"><span data-stu-id="5db6b-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5db6b-131">Zulässige Werte sind `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` und `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="5db6b-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`-w|--working-dir <WORKING_DIRECTORY>`**

  <span data-ttu-id="5db6b-132">Das Arbeitsverzeichnis, das vom Befehl verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5db6b-132">The working directory used by the command.</span></span> <span data-ttu-id="5db6b-133">Wenn nicht angegeben, wird das Unterverzeichnis *obj* des aktuellen Verzeichnisses verwendet.</span><span class="sxs-lookup"><span data-stu-id="5db6b-133">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="5db6b-134">Beispiele</span><span class="sxs-lookup"><span data-stu-id="5db6b-134">Examples</span></span>

- <span data-ttu-id="5db6b-135">Speichern Sie die in der Projektdatei *packages.csproj* für .NET Core 2.0.0 angegebenen Pakete:</span><span class="sxs-lookup"><span data-stu-id="5db6b-135">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --framework-version 2.0.0
  ```

- <span data-ttu-id="5db6b-136">Speichern Sie die in der Datei *packages.csproj* angegebenen Pakete ohne Optimierung:</span><span class="sxs-lookup"><span data-stu-id="5db6b-136">Store the packages specified in the *packages.csproj* without optimization:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --skip-optimization
  ```

## <a name="see-also"></a><span data-ttu-id="5db6b-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5db6b-137">See also</span></span>

- [<span data-ttu-id="5db6b-138">Laufzeitpaketspeicher</span><span class="sxs-lookup"><span data-stu-id="5db6b-138">Runtime package store</span></span>](../deploying/runtime-store.md)
