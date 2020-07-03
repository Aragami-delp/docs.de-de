---
ms.openlocfilehash: 00f89e6ae49982917fa7591c3283adec3947eed2
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365644"
---
### <a name="winforms-methods-now-throw-argumentnullexception"></a>WinForms-Methoden lösen jetzt ArgumentNullException aus

Einige Windows Forms-Methoden lösen nun eine <xref:System.ArgumentNullException>-Ausnahme für NULL-Argumente aus, für die sie zuvor eine <xref:System.NullReferenceException>-Ausnahme ausgelöst haben.

#### <a name="change-description"></a>Änderungsbeschreibung

Zuvor haben bestimmte Windows Forms-Methoden eine <xref:System.NullReferenceException>-Ausnahme ausgelöst, wenn ein Argument mit dem Wert NULL übergeben wurde. Ab .NET 5.0 lösen diese Methoden stattdessen eine <xref:System.ArgumentNullException>-Ausnahme für NULL-Argumente aus.

Das Auslösen einer <xref:System.ArgumentNullException>-Ausnahme entspricht dem Verhalten der .NET Runtime. Außerdem wird die Debugfunktion verbessert, indem ausdrücklich kommuniziert wird, dass ein Argument den Wert NULL aufweist und welches Argument betroffen ist.

#### <a name="version-introduced"></a>Eingeführt in Version

.NET 5.0

#### <a name="recommended-action"></a>Empfohlene Aktion

Wenn Sie eine dieser Methoden aufrufen und Ihr Code <xref:System.NullReferenceException> für NULL-Argumente abfängt, sollte stattdessen <xref:System.ArgumentNullException> abgefangen werden. Außerdem sollten Sie ein Update für den Code in Betracht ziehen, um die Übergabe von NULL-Argumenten an die aufgeführten Methoden zu verhindern.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Betroffene APIs

In der folgenden Tabelle sind die betroffenen Methoden und Parameter aufgeführt:

> [!div class="mx-tdBreakAll"]
> | Methode | Parametername | Hinzugefügte Version |
> |-|-|-|
> | <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)> | `owner` | 5.0 Preview 1 |
> | <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType> | `item` | 5.0 Preview 1 |
> | <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)> | `container` | 5.0 Preview 1 |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType> | `e` | 5.0 Preview 1 |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | 5.0 Preview 1 |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | 5.0 Preview 1 |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType> | `e` | 5.0 Preview 1 |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType> > | `e` | 5.0 Preview 1 |
> | <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType> | `dataGridViewCellStyle` | 5.0 Preview 2 |
> | <xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> | `data` | 5.0 Preview 2 |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | 5.0 Vorschau 5 |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | 5.0 Vorschau 5 |
> | <xref:System.Windows.Forms.ListViewGroup.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | `info` | 5.0 Vorschau 5 |
> | <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor(System.String,System.Int32,System.Int32)> | `className` | 5.0 Vorschau 5 |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | Version 5.0 Vorschau 6 |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Object[])> | `owner`, `value` | Version 5.0 Vorschau 6 |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)> | `owner`, `value` | Version 5.0 Vorschau 6 |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])?displayProperty=nameWithType> | `items` | Version 5.0 Vorschau 6 |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)?displayProperty=nameWithType> | `value` | Version 5.0 Vorschau 6 |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)?displayProperty=nameWithType> | `destination` | Version 5.0 Vorschau 6 |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.System%23Collections%23ICollection%23CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination`q` | Version 5.0 Vorschau 6 |

<!-- 

#### Affected APIs

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
- `M:System.Windows.Forms.ListViewGroup.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)`
- `M:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor(System.String,System.Int32,System.Int32)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.%23ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.System%23Collections%23ICollection%23CopyTo(System.Array,System.Int32)`

-->
