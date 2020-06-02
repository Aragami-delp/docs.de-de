---
title: 'Vorgehensweise: Veröffentlichen von Ereignissen, die den .NET Framework-Richtlinien entsprechen (C#-Programmierleitfaden)'
ms.date: 05/26/2020
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 137e52b80703491a4528a3eddc7fa12f9dce6f52
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144798"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a><span data-ttu-id="f699b-102">Vorgehensweise: Veröffentlichen von Ereignissen, die den .NET Framework-Richtlinien entsprechen (C#-Programmierleitfaden)</span><span class="sxs-lookup"><span data-stu-id="f699b-102">How to publish events that conform to .NET Framework Guidelines (C# Programming Guide)</span></span>

<span data-ttu-id="f699b-103">Das folgende Verfahren veranschaulicht, wie Sie Ereignisse hinzufügen können, die auf dem .NET Framework-Standardmuster ihrer Klassen und Strukturen basieren.</span><span class="sxs-lookup"><span data-stu-id="f699b-103">The following procedure demonstrates how to add events that follow the standard .NET Framework pattern to your classes and structs.</span></span> <span data-ttu-id="f699b-104">Alle Ereignisse in der .NET Framework-Klassenbibliothek basieren auf dem <xref:System.EventHandler>-Delegaten, der wie folgt definiert ist:</span><span class="sxs-lookup"><span data-stu-id="f699b-104">All events in the .NET Framework class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>

```csharp
public delegate void EventHandler(object sender, EventArgs e);
```

> [!NOTE]
> <span data-ttu-id="f699b-105">Das NET Framework 2.0 führt eine generische Version dieses Delegaten ein: <xref:System.EventHandler%601>.</span><span class="sxs-lookup"><span data-stu-id="f699b-105">The .NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="f699b-106">Die folgenden Beispiele zeigen, wie Sie beide Versionen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="f699b-106">The following examples show how to use both versions.</span></span>

<span data-ttu-id="f699b-107">Auch wenn Ereignisse in von Ihnen definierten Klassen auf jedem beliebigen Delegattyp basieren können – sogar Delegate, die einen Wert zurückgeben –, wird allgemein empfohlen, dass Sie für Ihre Ereignisse das .NET Framework-Muster mithilfe von <xref:System.EventHandler> verwenden. Dies wird im folgenden Beispiel veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="f699b-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET Framework pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>

<span data-ttu-id="f699b-108">Der Name `EventHandler` kann etwas Verwirrung stiften, da das Ereignis nicht tatsächlich verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="f699b-108">The name `EventHandler` can lead to a bit of confusion as it doesn't actually handle the event.</span></span> <span data-ttu-id="f699b-109"><xref:System.EventHandler> und der generische <xref:System.EventHandler%601> sind Delegattypen.</span><span class="sxs-lookup"><span data-stu-id="f699b-109">The <xref:System.EventHandler>, and generic <xref:System.EventHandler%601> are delegate types.</span></span> <span data-ttu-id="f699b-110">Eine Methode oder eine anonyme Funktion, deren Signatur mit der Delegatdefinition übereinstimmt, ist der *Ereignishandler* und wird aufgerufen, wenn das Ereignis ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="f699b-110">A method or lambda expression whose signature matches the delegate definition is the *event handler* and will be invoked when the event is raised.</span></span>

### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="f699b-111">So veröffentlichen Sie Ereignisse, die auf dem EventHandler-Muster basieren</span><span class="sxs-lookup"><span data-stu-id="f699b-111">To publish events based on the EventHandler pattern</span></span>

1. <span data-ttu-id="f699b-112">(Überspringen Sie diesen Schritt, und gehen Sie direkt zu Schritt 3a, wenn Sie keine benutzerdefinierten Daten mit Ihrem Ereignis senden müssen.) Deklarieren Sie die Klasse Ihrer benutzerdefinierten Daten in einem für Ihre Herausgeber- und Ihre Abonnentenklasse sichtbaren Geltungsbereich.</span><span class="sxs-lookup"><span data-stu-id="f699b-112">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="f699b-113">Fügen Sie dann die erforderlichen Member hinzu, die Ihre benutzerdefinierten Ereignisdaten enthalten sollen.</span><span class="sxs-lookup"><span data-stu-id="f699b-113">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="f699b-114">In diesem Beispiel wird eine einzelne Zeichenfolge zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="f699b-114">In this example, a simple string is returned.</span></span>

    ```csharp
    public class CustomEventArgs : EventArgs
    {
        public CustomEventArgs(string message)
        {
            Message = message;
        }

        public string Message { get; set; }
    }
    ```

2. <span data-ttu-id="f699b-115">(Überspringen Sie diesen Schritt, wenn Sie eine generische Version von <xref:System.EventHandler%601> verwenden.) Deklarieren Sie einen Delegaten in Ihrer Herausgeberklasse.</span><span class="sxs-lookup"><span data-stu-id="f699b-115">(Skip this step if you are using the generic version of <xref:System.EventHandler%601>.) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="f699b-116">Geben Sie ihm einen Namen, der auf `EventHandler` endet.</span><span class="sxs-lookup"><span data-stu-id="f699b-116">Give it a name that ends with `EventHandler`.</span></span> <span data-ttu-id="f699b-117">Der zweite Parameter gibt Ihren benutzerdefinierten `EventArgs`-Typ an.</span><span class="sxs-lookup"><span data-stu-id="f699b-117">The second parameter specifies your custom `EventArgs` type.</span></span>

    ```csharp
    public delegate void CustomEventHandler(object sender, CustomEventArgs args);
    ```

3. <span data-ttu-id="f699b-118">Deklarieren Sie das Ereignis in Ihrer Herausgeberklasse, indem Sie einen der folgenden Schritte verwenden.</span><span class="sxs-lookup"><span data-stu-id="f699b-118">Declare the event in your publishing class by using one of the following steps.</span></span>

    1. <span data-ttu-id="f699b-119">Wenn Sie keine benutzerdefinierte EventArgs-Klasse haben, ist Ihr Ereignistyp der nicht generische EventHandler-Delegat.</span><span class="sxs-lookup"><span data-stu-id="f699b-119">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="f699b-120">Sie müssen den Delegaten nicht deklarieren, da er schon im <xref:System>-Namespace deklariert wurde, der bei der Erstellung Ihres C#-Projekts erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="f699b-120">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="f699b-121">Fügen Sie den folgenden Code in Ihre Herausgeberklasse ein.</span><span class="sxs-lookup"><span data-stu-id="f699b-121">Add the following code to your publisher class.</span></span>

        ```csharp
        public event EventHandler RaiseCustomEvent;
        ```

    2. <span data-ttu-id="f699b-122">Wenn Sie die nicht generische Version von <xref:System.EventHandler> verwenden, und Sie eine benutzerdefinierte Klasse haben, die von <xref:System.EventArgs> abgeleitet ist, deklarieren Sie Ihr Ereignis innerhalb Ihrer Herausgeberklasse, und verwenden Sie Ihren Delegaten aus Schritt 2 als Typ.</span><span class="sxs-lookup"><span data-stu-id="f699b-122">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>

        ```csharp
        public event CustomEventHandler RaiseCustomEvent;
        ```

    3. <span data-ttu-id="f699b-123">Wenn sie die generische Version verwenden, benötigen Sie keinen benutzerdefinierten Delegaten.</span><span class="sxs-lookup"><span data-stu-id="f699b-123">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="f699b-124">Stattdessen geben Sie in Ihrer Herausgeberklasse Ihren Ereignistypen als `EventHandler<CustomEventArgs>` an und fügen den Namen Ihrer eigenen Klasse in die eckigen Klammern ein.</span><span class="sxs-lookup"><span data-stu-id="f699b-124">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>

        ```csharp
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;
        ```

## <a name="example"></a><span data-ttu-id="f699b-125">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f699b-125">Example</span></span>

<span data-ttu-id="f699b-126">Das folgende Beispiel veranschaulicht die oben genannten Schritte durch das Verwenden von einer benutzerdefinierten EventArgs-Klasse und von <xref:System.EventHandler%601> als Ereignistyp.</span><span class="sxs-lookup"><span data-stu-id="f699b-126">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>

[!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]

## <a name="see-also"></a><span data-ttu-id="f699b-127">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f699b-127">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="f699b-128">C#-Programmierhandbuch</span><span class="sxs-lookup"><span data-stu-id="f699b-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f699b-129">Ereignisse</span><span class="sxs-lookup"><span data-stu-id="f699b-129">Events</span></span>](index.md)
- [<span data-ttu-id="f699b-130">Delegaten</span><span class="sxs-lookup"><span data-stu-id="f699b-130">Delegates</span></span>](../delegates/index.md)
