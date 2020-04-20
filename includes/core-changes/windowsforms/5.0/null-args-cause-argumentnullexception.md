---
ms.openlocfilehash: fc0eec26073c299887b4748d0ad37e21c7294e84
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275242"
---
### <a name="winforms-apis-now-throw-argumentnullexception"></a><span data-ttu-id="e1a0a-101">WinForms-APIs lösen nun ArgumentNullException aus</span><span class="sxs-lookup"><span data-stu-id="e1a0a-101">WinForms APIs now throw ArgumentNullException</span></span>

<span data-ttu-id="e1a0a-102">Einige Windows Forms-Methoden lösen nun eine <xref:System.ArgumentNullException>-Ausnahme für NULL-Argumente aus, für die sie zuvor eine <xref:System.NullReferenceException>-Ausnahme ausgelöst haben.</span><span class="sxs-lookup"><span data-stu-id="e1a0a-102">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e1a0a-103">Änderungsbeschreibung</span><span class="sxs-lookup"><span data-stu-id="e1a0a-103">Change description</span></span>

<span data-ttu-id="e1a0a-104">Zuvor haben bestimmte Windows Forms-Methoden eine <xref:System.NullReferenceException>-Ausnahme ausgelöst, wenn ein Argument mit dem Wert NULL übergeben wurde.</span><span class="sxs-lookup"><span data-stu-id="e1a0a-104">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="e1a0a-105">Ab .NET 5.0 lösen diese Methoden stattdessen eine <xref:System.ArgumentNullException>-Ausnahme für NULL-Argumente aus.</span><span class="sxs-lookup"><span data-stu-id="e1a0a-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments instead.</span></span>

<span data-ttu-id="e1a0a-106">Das Auslösen einer <xref:System.ArgumentNullException>-Ausnahme entspricht dem Verhalten der .NET Runtime.</span><span class="sxs-lookup"><span data-stu-id="e1a0a-106">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="e1a0a-107">Außerdem wird die Debugfunktion verbessert, indem ausdrücklich kommuniziert wird, dass ein Argument den Wert NULL aufweist und welches Argument betroffen ist.</span><span class="sxs-lookup"><span data-stu-id="e1a0a-107">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e1a0a-108">Eingeführt in Version</span><span class="sxs-lookup"><span data-stu-id="e1a0a-108">Version introduced</span></span>

<span data-ttu-id="e1a0a-109">.NET 5.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="e1a0a-109">.NET 5.0 Preview 1\</span></span>
<span data-ttu-id="e1a0a-110">.NET 5.0 Preview 2</span><span class="sxs-lookup"><span data-stu-id="e1a0a-110">.NET 5.0 Preview 2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e1a0a-111">Empfohlene Aktion</span><span class="sxs-lookup"><span data-stu-id="e1a0a-111">Recommended action</span></span>

<span data-ttu-id="e1a0a-112">Wenn Sie eine dieser Methoden aufrufen und Ihr Code <xref:System.NullReferenceException> für NULL-Argumente abfängt, sollte stattdessen <xref:System.ArgumentNullException> abgefangen werden.</span><span class="sxs-lookup"><span data-stu-id="e1a0a-112">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="e1a0a-113">Außerdem sollten Sie ein Update für den Code in Betracht ziehen, um die Übergabe von NULL-Argumenten an die aufgeführten Methoden zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="e1a0a-113">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

#### <a name="category"></a><span data-ttu-id="e1a0a-114">Kategorie</span><span class="sxs-lookup"><span data-stu-id="e1a0a-114">Category</span></span>

<span data-ttu-id="e1a0a-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1a0a-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e1a0a-116">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="e1a0a-116">Affected APIs</span></span>

<span data-ttu-id="e1a0a-117">Ab .NET 5.0 Preview 1:</span><span class="sxs-lookup"><span data-stu-id="e1a0a-117">Starting in .NET 5.0 Preview 1:</span></span>

- <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)>
- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType>

<span data-ttu-id="e1a0a-118">Ab .NET 5.0 Preview 2:</span><span class="sxs-lookup"><span data-stu-id="e1a0a-118">Starting in .NET 5.0 Preview 2:</span></span>

- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType>
- <span data-ttu-id="e1a0a-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> (nur für den <xref:System.IO.Stream>-Parameter)</span><span class="sxs-lookup"><span data-stu-id="e1a0a-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> (for the <xref:System.IO.Stream> parameter only)</span></span>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Control.ControlCollection.#ctor(System.Windows.Forms.Control)`
- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.TableLayoutControlCollection.#ctor(System.Windows.Forms.TableLayoutPanel)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)`
- `M:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)`
- `M:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)`

-->
