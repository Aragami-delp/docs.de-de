---
title: Ereignisse – C#-Programmierhandbuch
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: e15c3d124b4d1c30e2f9bb9f44b40e25b6a72346
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240720"
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="24393-102">Ereignisse (C#-Programmierhandbuch)</span><span class="sxs-lookup"><span data-stu-id="24393-102">Events (C# Programming Guide)</span></span>
<span data-ttu-id="24393-103">Ereignisse aktivieren eine [Klasse](../../language-reference/keywords/class.md) oder ein Objekt, um Informationen über Aktionen von Interesse an andere Klassen oder Objekte zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="24393-103">Events enable a [class](../../language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="24393-104">Die Klasse, die das Ereignis sendet (oder *auslöst*), wird als *Herausgeber* bezeichnet, und die Klassen, die das Ereignis empfangen (oder *behandeln*), werden als *Abonnenten*bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="24393-104">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
<span data-ttu-id="24393-105">In einer typischen C#-Windows Forms oder Web-Anwendung abonnieren Sie Ereignisse, die von Steuerelementen wie Schaltflächen und Listenfelder ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="24393-105">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="24393-106">Sie können die integrierte Entwicklungsumgebung (IDE) von Visual C# zum Durchsuchen der Ereignisse verwenden, die ein Steuerelement auslöst, und diejenigen wählen, die Sie behandeln möchten.</span><span class="sxs-lookup"><span data-stu-id="24393-106">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="24393-107">Mithilfe der IDE können eine leere Ereignishandlermethode und der Code ganz einfach automatisch zu den Abonnenten des Ereignisses hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="24393-107">The IDE provides an easy way to automatically add an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="24393-108">Weitere Informationen finden Sie unter [Abonnieren von Ereignissen und Kündigen von Ereignisabonnements](./how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="24393-108">For more information, see [How to subscribe to and unsubscribe from events](./how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>
  
## <a name="events-overview"></a><span data-ttu-id="24393-109">Übersicht über Ereignisse</span><span class="sxs-lookup"><span data-stu-id="24393-109">Events Overview</span></span>  
 <span data-ttu-id="24393-110">Ereignisse verfügen über folgende Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="24393-110">Events have the following properties:</span></span>  
  
- <span data-ttu-id="24393-111">Der Herausgeber wird bestimmt, wenn ein Ereignis ausgelöst wird. Die Abonnenten bestimmen, welche Aktion als Reaktion auf das Ereignis ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="24393-111">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
- <span data-ttu-id="24393-112">Ein Ereignis kann mehrere Abonnenten haben.</span><span class="sxs-lookup"><span data-stu-id="24393-112">An event can have multiple subscribers.</span></span> <span data-ttu-id="24393-113">Ein Abonnent kann mehrere Ereignisse von mehreren Herausgebern behandeln.</span><span class="sxs-lookup"><span data-stu-id="24393-113">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
- <span data-ttu-id="24393-114">Ereignisse, die keine Abonnenten haben, werden nie ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="24393-114">Events that have no subscribers are never raised.</span></span>  
  
- <span data-ttu-id="24393-115">Ereignisse werden in der Regel verwendet, um Benutzeraktionen wie Mausklicks oder Menüauswahlen in GUI-Schnittstellen zu signalisieren.</span><span class="sxs-lookup"><span data-stu-id="24393-115">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
- <span data-ttu-id="24393-116">Wenn ein Ereignis mehrere Abonnenten hat, werden die Ereignishandler synchron aufgerufen, wenn ein Ereignis ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="24393-116">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="24393-117">Informationen zum asynchronen Aufrufen von Ereignissen finden Sie unter [Asynchrones Aufrufen von synchronen Methoden](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="24393-117">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
- <span data-ttu-id="24393-118">In der .NET Framework-Klassenbibliothek basieren Ereignisse auf dem <xref:System.EventHandler>-Delegaten und der <xref:System.EventArgs>-Basisklasse.</span><span class="sxs-lookup"><span data-stu-id="24393-118">In the .NET Framework class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="24393-119">Verwandte Abschnitte</span><span class="sxs-lookup"><span data-stu-id="24393-119">Related Sections</span></span>  
 <span data-ttu-id="24393-120">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="24393-120">For more information, see:</span></span>  
  
- [<span data-ttu-id="24393-121">Abonnieren von Ereignissen und Kündigen von Ereignisabonnements</span><span class="sxs-lookup"><span data-stu-id="24393-121">How to subscribe to and unsubscribe from events</span></span>](./how-to-subscribe-to-and-unsubscribe-from-events.md)

- [<span data-ttu-id="24393-122">Veröffentlichen von Ereignissen, die den .NET-Richtlinien entsprechen</span><span class="sxs-lookup"><span data-stu-id="24393-122">How to publish events that conform to .NET Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)

- [<span data-ttu-id="24393-123">Auslösen von Basisklassenereignissen in abgeleiteten Klassen</span><span class="sxs-lookup"><span data-stu-id="24393-123">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)

- [<span data-ttu-id="24393-124">Implementieren von Schnittstellenereignissen</span><span class="sxs-lookup"><span data-stu-id="24393-124">How to implement interface events</span></span>](./how-to-implement-interface-events.md)

- [<span data-ttu-id="24393-125">Implementieren benutzerdefinierter Ereignisaccessoren</span><span class="sxs-lookup"><span data-stu-id="24393-125">How to implement custom event accessors</span></span>](./how-to-implement-custom-event-accessors.md)

## <a name="c-language-specification"></a><span data-ttu-id="24393-126">C#-Programmiersprachenspezifikation</span><span class="sxs-lookup"><span data-stu-id="24393-126">C# Language Specification</span></span>  

<span data-ttu-id="24393-127">Weitere Informationen erhalten Sie unter [Ereignisse](~/_csharplang/spec/classes.md#events) in der [C#-Sprachspezifikation](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="24393-127">For more information, see [Events](~/_csharplang/spec/classes.md#events) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="24393-128">Die Sprachspezifikation ist die verbindliche Quelle für die Syntax und Verwendung von C#.</span><span class="sxs-lookup"><span data-stu-id="24393-128">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="featured-book-chapters"></a><span data-ttu-id="24393-129">Enthaltene Buchkapitel</span><span class="sxs-lookup"><span data-stu-id="24393-129">Featured Book Chapters</span></span>  
 <span data-ttu-id="24393-130">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) (Delegaten, Ereignisse und Lambda-Ausdrücke) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29) (C# 3.0-Cookbook, 3. Auflage: Mehr als 250 Lösungen für C# 3.0-Programmierer)</span><span class="sxs-lookup"><span data-stu-id="24393-130">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
 <span data-ttu-id="24393-131">[Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) (Delegaten und Ereignisse) in [Learning C# 3.0: Master the Fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29) (Erlernen von C# 3.0: Die Grundlagen von C# 3.0)</span><span class="sxs-lookup"><span data-stu-id="24393-131">[Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24393-132">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="24393-132">See also</span></span>

- <xref:System.EventHandler>
- [<span data-ttu-id="24393-133">C#-Programmierhandbuch</span><span class="sxs-lookup"><span data-stu-id="24393-133">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="24393-134">Delegaten</span><span class="sxs-lookup"><span data-stu-id="24393-134">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="24393-135">Erstellen von Ereignishandlern in Windows Forms</span><span class="sxs-lookup"><span data-stu-id="24393-135">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
