---
title: Neuerungen in .NET Core 3.1
description: Erfahren Sie mehr zu den neuen Features in .NET Core 3.1.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 08ae824b79ba6a1ff5a92a0b4306eabe5ccadfd2
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838308"
---
# <a name="whats-new-in-net-core-31"></a><span data-ttu-id="b8a6a-103">Neuerungen in .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="b8a6a-103">What's new in .NET Core 3.1</span></span>

<span data-ttu-id="b8a6a-104">In diesem Artikel werden Neuerungen in .NET Core 3.1 beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b8a6a-104">This article describes what is new in .NET Core 3.1.</span></span> <span data-ttu-id="b8a6a-105">Diese Version enthält kleinere Verbesserungen an .NET Core 3.0, wobei der Schwerpunkt auf kleinen, aber wichtigen Korrekturen liegt.</span><span class="sxs-lookup"><span data-stu-id="b8a6a-105">This release contains minor improvements to .NET Core 3.0, focusing on small, but important, fixes.</span></span> <span data-ttu-id="b8a6a-106">Das wichtigste Merkmal von .NET Core 3.1 ist, dass es sich um eine Version mit [langfristigem Support (Long-Term Support, LTS)](#long-term-support) handelt.</span><span class="sxs-lookup"><span data-stu-id="b8a6a-106">The most important feature about .NET Core 3.1 is that it's a [long-term support (LTS)](#long-term-support) release.</span></span>

<span data-ttu-id="b8a6a-107">Wenn Sie Visual Studio 2019 einsetzen, müssen Sie ein Update auf [Visual Studio 2019 16.4](https://visualstudio.microsoft.com/downloads/) durchführen, um mit .NET Core 3.1-Projekten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="b8a6a-107">If you're using Visual Studio 2019, you must update to [Visual Studio 2019 16.4](https://visualstudio.microsoft.com/downloads/) to work with .NET Core 3.1 projects.</span></span> <span data-ttu-id="b8a6a-108">Weitere Informationen zu Neuerungen in Visual Studio finden Sie im [Blog zu Visual Studio](https://devblogs.microsoft.com/visualstudio/tis-the-season-visual-studio-2019/).</span><span class="sxs-lookup"><span data-stu-id="b8a6a-108">For more information on what is new in Visual Studio, see the [Visual Studio Blog](https://devblogs.microsoft.com/visualstudio/tis-the-season-visual-studio-2019/).</span></span>

<span data-ttu-id="b8a6a-109">Visual Studio für Mac unterstützt und umfasst auch .NET Core 3.1, und zwar im Kanal für die Vorschauversion von Visual Studio für Mac 8.4.</span><span class="sxs-lookup"><span data-stu-id="b8a6a-109">Visual Studio for Mac also supports and includes .NET Core 3.1, in the Visual Studio for Mac 8.4 Preview channel.</span></span> <span data-ttu-id="b8a6a-110">Sie müssen den Kanal für die Vorschauversion abonnieren, um .NET Core 3.1 verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="b8a6a-110">You'll need to opt into the Preview channel to use .NET Core 3.1.</span></span>

<span data-ttu-id="b8a6a-111">Weitere Informationen zu dieser Version finden Sie unter [Ankündigung von .NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span><span class="sxs-lookup"><span data-stu-id="b8a6a-111">For more information about the release, see the [.NET Core 3.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

- <span data-ttu-id="b8a6a-112">[Laden Sie .NET Core 3.1 herunter](https://dotnet.microsoft.com/download/dotnet-core/3.1), um unter Windows, macOS oder Linux loszulegen.</span><span class="sxs-lookup"><span data-stu-id="b8a6a-112">[Download and get started with .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) on Windows, macOS, or Linux.</span></span>

## <a name="long-term-support"></a><span data-ttu-id="b8a6a-113">Langfristiger Support</span><span class="sxs-lookup"><span data-stu-id="b8a6a-113">Long-term support</span></span>

<span data-ttu-id="b8a6a-114">NET Core 3.1 ist eine LTS-Version mit Support von Microsoft für die nächsten drei Jahre.</span><span class="sxs-lookup"><span data-stu-id="b8a6a-114">.NET Core 3.1 is an LTS release with support from Microsoft for the next three years.</span></span> <span data-ttu-id="b8a6a-115">Es wird dringend empfohlen, Ihre Anwendungen auf .NET Core 3.1 umzustellen.</span><span class="sxs-lookup"><span data-stu-id="b8a6a-115">It's highly recommended that you move your apps to .NET Core 3.1.</span></span> <span data-ttu-id="b8a6a-116">Der aktuelle Lebenszyklus anderer Hauptversionen ist wie folgt:</span><span class="sxs-lookup"><span data-stu-id="b8a6a-116">The current lifecycle of other major releases is as follows:</span></span>

| <span data-ttu-id="b8a6a-117">Freigabe</span><span class="sxs-lookup"><span data-stu-id="b8a6a-117">Release</span></span> | <span data-ttu-id="b8a6a-118">Hinweis</span><span class="sxs-lookup"><span data-stu-id="b8a6a-118">Note</span></span> |
| ------- | ---- |
| <span data-ttu-id="b8a6a-119">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b8a6a-119">.NET Core 3.0</span></span> | <span data-ttu-id="b8a6a-120">Ende des Lebenszyklus: 03. März 2020</span><span class="sxs-lookup"><span data-stu-id="b8a6a-120">End of life on March 3, 2020.</span></span>     |
| <span data-ttu-id="b8a6a-121">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="b8a6a-121">.NET Core 2.2</span></span> | <span data-ttu-id="b8a6a-122">Ende des Lebenszyklus: 23. Dezember 2019</span><span class="sxs-lookup"><span data-stu-id="b8a6a-122">End of life on December 23, 2019.</span></span> |
| <span data-ttu-id="b8a6a-123">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b8a6a-123">.NET Core 2.1</span></span> | <span data-ttu-id="b8a6a-124">Ende des Lebenszyklus: 21. August 2021</span><span class="sxs-lookup"><span data-stu-id="b8a6a-124">End of life on August 21, 2021.</span></span>    |

<span data-ttu-id="b8a6a-125">Weitere Informationen finden Sie in der [Supportrichtlinie für .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="b8a6a-125">For more information, see the [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="windows-forms"></a><span data-ttu-id="b8a6a-126">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b8a6a-126">Windows Forms</span></span>

<span data-ttu-id="b8a6a-127">*Nur Windows*</span><span class="sxs-lookup"><span data-stu-id="b8a6a-127">*Windows only*</span></span>

> [!WARNING]
> <span data-ttu-id="b8a6a-128">Bei Windows Forms gibt es Breaking Changes.</span><span class="sxs-lookup"><span data-stu-id="b8a6a-128">There are breaking changes in Windows Forms.</span></span>

<span data-ttu-id="b8a6a-129">Windows Forms wurden ältere Steuerelemente hinzugefügt, die in der Visual Studio Designer-Toolbox seit einiger Zeit nicht mehr verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="b8a6a-129">Legacy controls were included in Windows Forms that have been unavailable in the Visual Studio Designer Toolbox for some time.</span></span> <span data-ttu-id="b8a6a-130">Diese wurden bereits in .NET Framework 2.0 durch neue Steuerelemente ersetzt.</span><span class="sxs-lookup"><span data-stu-id="b8a6a-130">These were replaced with new controls back in .NET Framework 2.0.</span></span> <span data-ttu-id="b8a6a-131">Sie wurden aus dem Desktop SDK für .NET Core 3.1 entfernt.</span><span class="sxs-lookup"><span data-stu-id="b8a6a-131">These have been removed from the Desktop SDK for .NET Core 3.1.</span></span>

| <span data-ttu-id="b8a6a-132">Entferntes Steuerelement</span><span class="sxs-lookup"><span data-stu-id="b8a6a-132">Removed control</span></span> | <span data-ttu-id="b8a6a-133">Empfohlener Ersatz</span><span class="sxs-lookup"><span data-stu-id="b8a6a-133">Recommended replacement</span></span> | <span data-ttu-id="b8a6a-134">Zugehörige entfernte APIs</span><span class="sxs-lookup"><span data-stu-id="b8a6a-134">Associated APIs removed</span></span> |
| --------------- | ----------------------- | ----------------------- |
| <span data-ttu-id="b8a6a-135">DataGrid</span><span class="sxs-lookup"><span data-stu-id="b8a6a-135">DataGrid</span></span>        | <xref:System.Windows.Forms.DataGridView>      | <span data-ttu-id="b8a6a-136">DataGridCell</span><span class="sxs-lookup"><span data-stu-id="b8a6a-136">DataGridCell</span></span><br/><span data-ttu-id="b8a6a-137">DataGridRow</span><span class="sxs-lookup"><span data-stu-id="b8a6a-137">DataGridRow</span></span><br/><span data-ttu-id="b8a6a-138">DataGridTableCollection</span><span class="sxs-lookup"><span data-stu-id="b8a6a-138">DataGridTableCollection</span></span><br/><span data-ttu-id="b8a6a-139">DataGridColumnCollection</span><span class="sxs-lookup"><span data-stu-id="b8a6a-139">DataGridColumnCollection</span></span><br/><span data-ttu-id="b8a6a-140">DataGridTableStyle</span><span class="sxs-lookup"><span data-stu-id="b8a6a-140">DataGridTableStyle</span></span><br/><span data-ttu-id="b8a6a-141">DataGridColumnStyle</span><span class="sxs-lookup"><span data-stu-id="b8a6a-141">DataGridColumnStyle</span></span><br/><span data-ttu-id="b8a6a-142">DataGridLineStyle</span><span class="sxs-lookup"><span data-stu-id="b8a6a-142">DataGridLineStyle</span></span><br/><span data-ttu-id="b8a6a-143">DataGridParentRowsLabel</span><span class="sxs-lookup"><span data-stu-id="b8a6a-143">DataGridParentRowsLabel</span></span><br/><span data-ttu-id="b8a6a-144">DataGridParentRowsLabelStyle</span><span class="sxs-lookup"><span data-stu-id="b8a6a-144">DataGridParentRowsLabelStyle</span></span><br/><span data-ttu-id="b8a6a-145">DataGridBoolColumn</span><span class="sxs-lookup"><span data-stu-id="b8a6a-145">DataGridBoolColumn</span></span><br/><span data-ttu-id="b8a6a-146">DataGridTextBox</span><span class="sxs-lookup"><span data-stu-id="b8a6a-146">DataGridTextBox</span></span><br/><span data-ttu-id="b8a6a-147">GridColumnStylesCollection</span><span class="sxs-lookup"><span data-stu-id="b8a6a-147">GridColumnStylesCollection</span></span><br/><span data-ttu-id="b8a6a-148">GridTableStylesCollection</span><span class="sxs-lookup"><span data-stu-id="b8a6a-148">GridTableStylesCollection</span></span><br/><span data-ttu-id="b8a6a-149">HitTestType</span><span class="sxs-lookup"><span data-stu-id="b8a6a-149">HitTestType</span></span> |
| <span data-ttu-id="b8a6a-150">ToolBar</span><span class="sxs-lookup"><span data-stu-id="b8a6a-150">ToolBar</span></span>         | <xref:System.Windows.Forms.ToolStrip>         | <span data-ttu-id="b8a6a-151">ToolBarAppearance</span><span class="sxs-lookup"><span data-stu-id="b8a6a-151">ToolBarAppearance</span></span> |
| <span data-ttu-id="b8a6a-152">ToolBarButton</span><span class="sxs-lookup"><span data-stu-id="b8a6a-152">ToolBarButton</span></span>   | <xref:System.Windows.Forms.ToolStripButton>   | <span data-ttu-id="b8a6a-153">ToolBarButtonClickEventArgs</span><span class="sxs-lookup"><span data-stu-id="b8a6a-153">ToolBarButtonClickEventArgs</span></span><br/><span data-ttu-id="b8a6a-154">ToolBarButtonClickEventHandler</span><span class="sxs-lookup"><span data-stu-id="b8a6a-154">ToolBarButtonClickEventHandler</span></span><br/><span data-ttu-id="b8a6a-155">ToolBarButtonStyle</span><span class="sxs-lookup"><span data-stu-id="b8a6a-155">ToolBarButtonStyle</span></span><br/><span data-ttu-id="b8a6a-156">ToolBarTextAlign</span><span class="sxs-lookup"><span data-stu-id="b8a6a-156">ToolBarTextAlign</span></span> |
| <span data-ttu-id="b8a6a-157">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="b8a6a-157">ContextMenu</span></span>     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | <span data-ttu-id="b8a6a-158">MenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="b8a6a-158">MenuItemCollection</span></span> |
| <span data-ttu-id="b8a6a-159">MainMenu</span><span class="sxs-lookup"><span data-stu-id="b8a6a-159">MainMenu</span></span>        | <xref:System.Windows.Forms.MenuStrip>         |  |
| <span data-ttu-id="b8a6a-160">MenuItem</span><span class="sxs-lookup"><span data-stu-id="b8a6a-160">MenuItem</span></span>        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

<span data-ttu-id="b8a6a-161">Es wird empfohlen, Ihre Anwendungen auf .NET Core 3.1 zu aktualisieren und auf die Ersatzsteuerelemente umzusteigen.</span><span class="sxs-lookup"><span data-stu-id="b8a6a-161">We recommend you update your applications to .NET Core 3.1 and move to the replacement controls.</span></span> <span data-ttu-id="b8a6a-162">Das Ersetzen der Steuerelemente ist ein unkomplizierter Prozess, der im Wesentlichen das Suchen und Ersetzen des jeweiligen Typs vorsieht.</span><span class="sxs-lookup"><span data-stu-id="b8a6a-162">Replacing the controls is a straightforward process, essentially "find and replace" on the type.</span></span>

## <a name="ccli"></a><span data-ttu-id="b8a6a-163">C++/CLI</span><span class="sxs-lookup"><span data-stu-id="b8a6a-163">C++/CLI</span></span>

<span data-ttu-id="b8a6a-164">*Nur Windows*</span><span class="sxs-lookup"><span data-stu-id="b8a6a-164">*Windows only*</span></span>

<span data-ttu-id="b8a6a-165">Es wurde Unterstützung für die Erstellung von C++/CLI-Projekten (auch „verwaltete C++-Projekte“ genannt) hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="b8a6a-165">Support has been added for creating C++/CLI (also known as "managed C++") projects.</span></span> <span data-ttu-id="b8a6a-166">Die im Rahmen dieser Projekte erstellten Binärdateien sind mit .NET Core 3.0 und höheren Versionen kompatibel.</span><span class="sxs-lookup"><span data-stu-id="b8a6a-166">Binaries produced from these projects are compatible with .NET Core 3.0 and later versions.</span></span>

<span data-ttu-id="b8a6a-167">Um Unterstützung für C++/CLI in Visual Studio 2019 16.4 hinzuzufügen, installieren Sie die [Workload „Desktopentwicklung mit C++“](https://docs.microsoft.com/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span><span class="sxs-lookup"><span data-stu-id="b8a6a-167">To add support for C++/CLI in Visual Studio 2019 16.4, install the [Desktop development with C++ workload](https://docs.microsoft.com/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span></span> <span data-ttu-id="b8a6a-168">Diese Workload fügt Visual Studio zwei Vorlagen hinzu:</span><span class="sxs-lookup"><span data-stu-id="b8a6a-168">This workload adds two templates to Visual Studio:</span></span>

- <span data-ttu-id="b8a6a-169">CLR-Klassenbibliothek (.NET Core)</span><span class="sxs-lookup"><span data-stu-id="b8a6a-169">CLR Class Library (.NET Core)</span></span>
- <span data-ttu-id="b8a6a-170">Leeres CLR-Projekt (.NET Core)</span><span class="sxs-lookup"><span data-stu-id="b8a6a-170">CLR Empty Project (.NET Core)</span></span>

## <a name="next-steps"></a><span data-ttu-id="b8a6a-171">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="b8a6a-171">Next steps</span></span>

- [<span data-ttu-id="b8a6a-172">Breaking Changes bei der Migration von Version 3.0 zu Version 3.1</span><span class="sxs-lookup"><span data-stu-id="b8a6a-172">Review the breaking changes between .NET Core 3.0 and 3.1.</span></span>](../compatibility/3.0-3.1.md)
- [<span data-ttu-id="b8a6a-173">Informationen zu den wichtigsten Unterschieden zwischen .NET Framework und .NET Core 3.0 für Windows Forms-Apps</span><span class="sxs-lookup"><span data-stu-id="b8a6a-173">Review the breaking changes between .NET Framework and .NET Core 3.0 for Windows Forms apps.</span></span>](../porting/winforms-breaking-changes.md)