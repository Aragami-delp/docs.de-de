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
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a>Vorgehensweise: Veröffentlichen von Ereignissen, die den .NET Framework-Richtlinien entsprechen (C#-Programmierleitfaden)

Das folgende Verfahren veranschaulicht, wie Sie Ereignisse hinzufügen können, die auf dem .NET Framework-Standardmuster ihrer Klassen und Strukturen basieren. Alle Ereignisse in der .NET Framework-Klassenbibliothek basieren auf dem <xref:System.EventHandler>-Delegaten, der wie folgt definiert ist:

```csharp
public delegate void EventHandler(object sender, EventArgs e);
```

> [!NOTE]
> Das NET Framework 2.0 führt eine generische Version dieses Delegaten ein: <xref:System.EventHandler%601>. Die folgenden Beispiele zeigen, wie Sie beide Versionen verwenden können.

Auch wenn Ereignisse in von Ihnen definierten Klassen auf jedem beliebigen Delegattyp basieren können – sogar Delegate, die einen Wert zurückgeben –, wird allgemein empfohlen, dass Sie für Ihre Ereignisse das .NET Framework-Muster mithilfe von <xref:System.EventHandler> verwenden. Dies wird im folgenden Beispiel veranschaulicht.

Der Name `EventHandler` kann etwas Verwirrung stiften, da das Ereignis nicht tatsächlich verarbeitet wird. <xref:System.EventHandler> und der generische <xref:System.EventHandler%601> sind Delegattypen. Eine Methode oder eine anonyme Funktion, deren Signatur mit der Delegatdefinition übereinstimmt, ist der *Ereignishandler* und wird aufgerufen, wenn das Ereignis ausgelöst wird.

### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a>So veröffentlichen Sie Ereignisse, die auf dem EventHandler-Muster basieren

1. (Überspringen Sie diesen Schritt, und gehen Sie direkt zu Schritt 3a, wenn Sie keine benutzerdefinierten Daten mit Ihrem Ereignis senden müssen.) Deklarieren Sie die Klasse Ihrer benutzerdefinierten Daten in einem für Ihre Herausgeber- und Ihre Abonnentenklasse sichtbaren Geltungsbereich. Fügen Sie dann die erforderlichen Member hinzu, die Ihre benutzerdefinierten Ereignisdaten enthalten sollen. In diesem Beispiel wird eine einzelne Zeichenfolge zurückgegeben.

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

2. (Überspringen Sie diesen Schritt, wenn Sie eine generische Version von <xref:System.EventHandler%601> verwenden.) Deklarieren Sie einen Delegaten in Ihrer Herausgeberklasse. Geben Sie ihm einen Namen, der auf `EventHandler` endet. Der zweite Parameter gibt Ihren benutzerdefinierten `EventArgs`-Typ an.

    ```csharp
    public delegate void CustomEventHandler(object sender, CustomEventArgs args);
    ```

3. Deklarieren Sie das Ereignis in Ihrer Herausgeberklasse, indem Sie einen der folgenden Schritte verwenden.

    1. Wenn Sie keine benutzerdefinierte EventArgs-Klasse haben, ist Ihr Ereignistyp der nicht generische EventHandler-Delegat. Sie müssen den Delegaten nicht deklarieren, da er schon im <xref:System>-Namespace deklariert wurde, der bei der Erstellung Ihres C#-Projekts erstellt wird. Fügen Sie den folgenden Code in Ihre Herausgeberklasse ein.

        ```csharp
        public event EventHandler RaiseCustomEvent;
        ```

    2. Wenn Sie die nicht generische Version von <xref:System.EventHandler> verwenden, und Sie eine benutzerdefinierte Klasse haben, die von <xref:System.EventArgs> abgeleitet ist, deklarieren Sie Ihr Ereignis innerhalb Ihrer Herausgeberklasse, und verwenden Sie Ihren Delegaten aus Schritt 2 als Typ.

        ```csharp
        public event CustomEventHandler RaiseCustomEvent;
        ```

    3. Wenn sie die generische Version verwenden, benötigen Sie keinen benutzerdefinierten Delegaten. Stattdessen geben Sie in Ihrer Herausgeberklasse Ihren Ereignistypen als `EventHandler<CustomEventArgs>` an und fügen den Namen Ihrer eigenen Klasse in die eckigen Klammern ein.

        ```csharp
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;
        ```

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die oben genannten Schritte durch das Verwenden von einer benutzerdefinierten EventArgs-Klasse und von <xref:System.EventHandler%601> als Ereignistyp.

[!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]

## <a name="see-also"></a>Siehe auch

- <xref:System.Delegate>
- [C#-Programmierhandbuch](../index.md)
- [Ereignisse](index.md)
- [Delegaten](../delegates/index.md)
