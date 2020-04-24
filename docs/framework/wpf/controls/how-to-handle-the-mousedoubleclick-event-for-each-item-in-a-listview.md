---
title: 'Gewusst wie: Behandeln des MouseDoubleClick-Ereignisses für die einzelnen ListView-Einträge'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7bbc7bad36b3b1f2c92065e5f5699e5a86ac6189
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646110"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a><span data-ttu-id="ef1db-102">Gewusst wie: Behandeln des MouseDoubleClick-Ereignisses für die einzelnen ListView-Einträge</span><span class="sxs-lookup"><span data-stu-id="ef1db-102">How to: Handle the MouseDoubleClick Event for Each Item in a ListView</span></span>
<span data-ttu-id="ef1db-103">Um ein Ereignis für ein <xref:System.Windows.Controls.ListView>Element in einem zu behandeln, müssen Sie jedem <xref:System.Windows.Controls.ListViewItem>einen Ereignishandler hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ef1db-103">To handle an event for an item in a <xref:System.Windows.Controls.ListView>, you need to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span> <span data-ttu-id="ef1db-104">Wenn <xref:System.Windows.Controls.ListView> a an eine Datenquelle gebunden ist, erstellen <xref:System.Windows.Controls.ListViewItem>Sie nicht explizit eine , aber <xref:System.Windows.EventSetter> Sie können das <xref:System.Windows.Controls.ListViewItem>Ereignis für jedes Element behandeln, indem Sie einem Stil einer hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ef1db-104">When a <xref:System.Windows.Controls.ListView> is bound to a data source, you don't explicitly create a <xref:System.Windows.Controls.ListViewItem>, but you can handle the event for each item by adding an <xref:System.Windows.EventSetter> to a style of a <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef1db-105">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ef1db-105">Example</span></span>  
 <span data-ttu-id="ef1db-106">Im folgenden Beispiel wird <xref:System.Windows.Controls.ListView> eine datengebundene und erstellte erstellt, <xref:System.Windows.Style> um jedem <xref:System.Windows.Controls.ListViewItem>einen Ereignishandler hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="ef1db-106">The following example creates a data-bound <xref:System.Windows.Controls.ListView> and creates a <xref:System.Windows.Style> to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="ef1db-107">Im folgenden Beispiel <xref:System.Windows.Controls.Control.MouseDoubleClick> wird das Ereignis behandelt.</span><span class="sxs-lookup"><span data-stu-id="ef1db-107">The following example handles the <xref:System.Windows.Controls.Control.MouseDoubleClick> event.</span></span>  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> <span data-ttu-id="ef1db-108">Obwohl es am häufigsten <xref:System.Windows.Controls.ListView> ist, eine an eine Datenquelle zu binden, können <xref:System.Windows.Controls.ListViewItem> Sie einen Stil <xref:System.Windows.Controls.ListView> verwenden, um jedem <xref:System.Windows.Controls.ListViewItem>Ereignishandler in einer nicht datengebundenen Datei einen Ereignishandler hinzuzufügen, unabhängig davon, ob Sie explizit eine erstellen.</span><span class="sxs-lookup"><span data-stu-id="ef1db-108">Although it is most common to bind a <xref:System.Windows.Controls.ListView> to a data source, you can use a style to add an event handler to each <xref:System.Windows.Controls.ListViewItem> in a non-data-bound <xref:System.Windows.Controls.ListView> regardless of whether you explicitly create a <xref:System.Windows.Controls.ListViewItem>.</span></span>  <span data-ttu-id="ef1db-109">Weitere Informationen zu explizit und <xref:System.Windows.Controls.ListViewItem> implizit <xref:System.Windows.Controls.ItemsControl>erstellten Steuerelementen finden Sie unter .</span><span class="sxs-lookup"><span data-stu-id="ef1db-109">For more information about explicitly and implicitly created <xref:System.Windows.Controls.ListViewItem> controls, see <xref:System.Windows.Controls.ItemsControl>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef1db-110">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ef1db-110">See also</span></span>

- <xref:System.Xml.XmlElement>
- [<span data-ttu-id="ef1db-111">Datenbindung sübersicht</span><span class="sxs-lookup"><span data-stu-id="ef1db-111">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="ef1db-112">Erstellen von Formaten und Vorlagen</span><span class="sxs-lookup"><span data-stu-id="ef1db-112">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="ef1db-113">Binden an XML-Daten mithilfe eines XMLDataProvider- und XPath-Abfragen</span><span class="sxs-lookup"><span data-stu-id="ef1db-113">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="ef1db-114">Übersicht über ListView</span><span class="sxs-lookup"><span data-stu-id="ef1db-114">ListView Overview</span></span>](listview-overview.md)
