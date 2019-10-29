---
title: Laden von Abhängigkeiten – .NET Core
description: Übersicht über das verwaltete und nicht verwaltete Laden von Abhängigkeiten in .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: 0388bd1fa29ce1caad93c917503dac9eed8974e1
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2019
ms.locfileid: "72303665"
---
# <a name="dependency-loading-in-net-core"></a><span data-ttu-id="851da-103">Laden von Abhängigkeiten in .NET Core</span><span class="sxs-lookup"><span data-stu-id="851da-103">Dependency loading in .NET Core</span></span>

<span data-ttu-id="851da-104">Jede .NET Core-Anwendung weist Abhängigkeiten auf.</span><span class="sxs-lookup"><span data-stu-id="851da-104">Every .NET Core application has dependencies.</span></span> <span data-ttu-id="851da-105">Selbst die einfache `hello world`-App wiest Abhängigkeiten von Teilen der .NET Core-Klassenbibliotheken auf.</span><span class="sxs-lookup"><span data-stu-id="851da-105">Even the simple `hello world` app has dependencies on portions of the .NET Core class libraries.</span></span>

<span data-ttu-id="851da-106">Das Verständnis der Logik hinter dem Laden von .NET Core-Standardassemblys kann beim Verstehen und Debuggen gängiger Bereitstellungsprobleme helfen.</span><span class="sxs-lookup"><span data-stu-id="851da-106">Understanding .NET Core default assembly loading logic can help understanding and debugging typical deployment issues.</span></span>

<span data-ttu-id="851da-107">In einigen Anwendungen werden Abhängigkeiten dynamisch zur Laufzeit festgelegt.</span><span class="sxs-lookup"><span data-stu-id="851da-107">In some applications, dependencies are dynamically determined at runtime.</span></span> <span data-ttu-id="851da-108">In diesen Fällen ist es wichtig zu verstehen, wie verwaltete Assemblys und nicht verwaltete Abhängigkeiten geladen werden.</span><span class="sxs-lookup"><span data-stu-id="851da-108">In these situations, it's critical to understand how managed assemblies and unmanaged dependencies are loaded.</span></span>

## <a name="understanding-assemblyloadcontext"></a><span data-ttu-id="851da-109">Grundlegendes zu AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="851da-109">Understanding AssemblyLoadContext</span></span>

<span data-ttu-id="851da-110">Die <xref:System.Runtime.Loader.AssemblyLoadContext>-API ist für das Laden in .NET Core von zentraler Bedeutung.</span><span class="sxs-lookup"><span data-stu-id="851da-110">The <xref:System.Runtime.Loader.AssemblyLoadContext> API is central to the .NET Core loading design.</span></span> <span data-ttu-id="851da-111">Der Artikel [Grundlegendes zu AssemblyLoadContext](understanding-assemblyloadcontext.md) enthält eine konzeptionelle Übersicht über den Entwurf.</span><span class="sxs-lookup"><span data-stu-id="851da-111">The [Understanding AssemblyLoadContext](understanding-assemblyloadcontext.md) article provides a conceptual overview to the design.</span></span>

## <a name="loading-details"></a><span data-ttu-id="851da-112">Laden von Details</span><span class="sxs-lookup"><span data-stu-id="851da-112">Loading details</span></span>

<span data-ttu-id="851da-113">Details zum Ladealgorithmus werden in mehreren Artikeln kurz behandelt:</span><span class="sxs-lookup"><span data-stu-id="851da-113">The loading algorithm details are covered briefly in several articles:</span></span>

- [<span data-ttu-id="851da-114">Ladealgorithmus für verwaltete Assemblys</span><span class="sxs-lookup"><span data-stu-id="851da-114">Managed assembly loading algorithm</span></span>](loading-managed.md)
- [<span data-ttu-id="851da-115">Ladealgorithmus für Satellitenassemblys</span><span class="sxs-lookup"><span data-stu-id="851da-115">Satellite assembly loading algorithm</span></span>](loading-resources.md)
- [<span data-ttu-id="851da-116">Ladealgorithmus für nicht verwaltete (native) Bibliotheken</span><span class="sxs-lookup"><span data-stu-id="851da-116">Unmanaged (native) library loading algorithm</span></span>](loading-unmanaged.md)
- [<span data-ttu-id="851da-117">Standardüberprüfung</span><span class="sxs-lookup"><span data-stu-id="851da-117">Default probing</span></span>](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="851da-118">Erstellen einer .NET Core-Anwendung mit Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="851da-118">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="851da-119">Im Tutorial [Erstellen einer .NET Core-Anwendung mit Plug-Ins](../tutorials/creating-app-with-plugin-support.md) wird beschrieben, wie ein benutzerdefinierter AssemblyLoadContext erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="851da-119">The tutorial [Create a .NET Core application with plugins](../tutorials/creating-app-with-plugin-support.md) describes how to create a custom AssemblyLoadContext.</span></span> <span data-ttu-id="851da-120">Er verwendet einen <xref:System.Runtime.Loader.AssemblyDependencyResolver>, um die Abhängigkeiten des Plug-Ins aufzulösen.</span><span class="sxs-lookup"><span data-stu-id="851da-120">It uses an <xref:System.Runtime.Loader.AssemblyDependencyResolver> to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="851da-121">Das Tutorial isoliert die Plug-In-Abhängigkeiten ordnungsgemäß von der Hostanwendung.</span><span class="sxs-lookup"><span data-stu-id="851da-121">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span>

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="851da-122">Verwenden und Debuggen von Assemblyentladbarkeit in .NET Core</span><span class="sxs-lookup"><span data-stu-id="851da-122">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="851da-123">Der Artikel [Verwenden und Debuggen der Entladbarkeit von Assemblys in .NET Core](../../standard/assembly/unloadability-howto.md) enthält ein ausführliches Tutorial.</span><span class="sxs-lookup"><span data-stu-id="851da-123">The [How to use and debug assembly unloadability in .NET Core](../../standard/assembly/unloadability-howto.md) article is a step-by-step tutorial.</span></span> <span data-ttu-id="851da-124">Darin wird gezeigt, wie Sie eine .NET Core-Anwendung laden, ausführen und dann entladen.</span><span class="sxs-lookup"><span data-stu-id="851da-124">It shows how to load a .NET Core application, execute, and then unload it.</span></span> <span data-ttu-id="851da-125">Der Artikel enthält auch Tipps zum Debuggen.</span><span class="sxs-lookup"><span data-stu-id="851da-125">The article also provides debugging tips.</span></span>