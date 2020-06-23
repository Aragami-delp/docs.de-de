---
title: 'Vorgehensweise: Asynchrones Aufrufen von WCF-Dienstvorgängen'
description: Erfahren Sie, wie Sie einen WCF-Client erstellen, der asynchron auf einen Dienst Vorgang zugreifen kann, indem Sie das ereignisgesteuerte asynchrone Aufruf Modell verwenden.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: aa31f64473111800f4cd01907a0446c94f368456
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247233"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="32096-103">Vorgehensweise: Asynchrones Aufrufen von WCF-Dienstvorgängen</span><span class="sxs-lookup"><span data-stu-id="32096-103">How to: Call WCF Service Operations Asynchronously</span></span>

<span data-ttu-id="32096-104">In diesem Artikel wird beschrieben, wie ein Client auf einen Dienst Vorgang asynchron zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="32096-104">This article covers how a client can access a service operation asynchronously.</span></span> <span data-ttu-id="32096-105">Der Dienst in diesem Artikel implementiert die- `ICalculator` Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="32096-105">The service in this article implements the `ICalculator` interface.</span></span> <span data-ttu-id="32096-106">Der Client kann mithilfe des ereignisgesteuerten asynchronen Aufrufmodells die Vorgänge asynchron an dieser Schnittstelle aufrufen.</span><span class="sxs-lookup"><span data-stu-id="32096-106">The client can call the operations on this interface asynchronously by using the event-driven asynchronous calling model.</span></span> <span data-ttu-id="32096-107">(Weitere Informationen über das ereignisbasierte asynchrone Aufruf Modell finden Sie unter [Multithreadprogrammierung mit dem ereignisbasierten asynchronen Muster](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)).</span><span class="sxs-lookup"><span data-stu-id="32096-107">(For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)).</span></span> <span data-ttu-id="32096-108">Ein Beispiel für das asynchrone Implementieren eines Vorgangs in einem Dienst finden Sie unter Gewusst [wie: Implementieren eines asynchronen Dienst Vorgangs](../how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="32096-108">For an example that shows how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="32096-109">Weitere Informationen zu synchronen und asynchronen Vorgängen finden Sie unter [synchrone und asynchrone Vorgänge](../synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="32096-109">For more information about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../synchronous-and-asynchronous-operations.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="32096-110">Bei Verwendung einer <xref:System.ServiceModel.ChannelFactory%601> wird das ereignisgesteuerte asynchrone Aufrufmodell nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="32096-110">The event-driven asynchronous calling model is not supported when using a <xref:System.ServiceModel.ChannelFactory%601>.</span></span> <span data-ttu-id="32096-111">Weitere Informationen zum Ausführen von asynchronen Aufrufen mithilfe von finden Sie unter Gewusst <xref:System.ServiceModel.ChannelFactory%601> [wie: Asynchrones Aufrufen von Vorgängen mithilfe einer Kanalfactory](how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="32096-111">For information about making asynchronous calls using the <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="32096-112">Vorgehensweise</span><span class="sxs-lookup"><span data-stu-id="32096-112">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="32096-113">So rufen Sie WCF-Dienstvorgänge asynchron auf</span><span class="sxs-lookup"><span data-stu-id="32096-113">To call WCF service operations asynchronously</span></span>  
  
1. <span data-ttu-id="32096-114">Führen Sie das [Service Model Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) -Tool mit den `/async` `/tcv:Version35` Befehlsoptionen und aus, wie im folgenden Befehl gezeigt.</span><span class="sxs-lookup"><span data-stu-id="32096-114">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool with both the `/async` and the `/tcv:Version35` command options together as shown in the following command.</span></span>  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     <span data-ttu-id="32096-115">Dies generiert zusätzlich zu den synchronen und standardmäßigen delegatbasierten asynchronen Vorgängen eine WCF-Client Klasse, die Folgendes enthält:</span><span class="sxs-lookup"><span data-stu-id="32096-115">This generates, in addition to the synchronous and standard delegate-based asynchronous operations, a WCF client class that contains:</span></span>  
  
    - <span data-ttu-id="32096-116">Zwei <`operationName` > `Async` Vorgänge für die Verwendung mit dem ereignisbasierten asynchronen Aufruf Ansatz.</span><span class="sxs-lookup"><span data-stu-id="32096-116">Two <`operationName`>`Async` operations for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="32096-117">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="32096-117">For example:</span></span>  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - <span data-ttu-id="32096-118">Der Vorgang hat Ereignisse der Form <`operationName` > `Completed` für die Verwendung mit dem ereignisbasierten asynchronen Aufruf Ansatz verwendet.</span><span class="sxs-lookup"><span data-stu-id="32096-118">Operation completed events of the form <`operationName`>`Completed` for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="32096-119">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="32096-119">For example:</span></span>  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <span data-ttu-id="32096-120"><xref:System.EventArgs?displayProperty=nameWithType>Typen für jeden Vorgang (in der Form <`operationName` > `CompletedEventArgs` ) für die Verwendung mit dem ereignisbasierten asynchronen Aufruf Ansatz.</span><span class="sxs-lookup"><span data-stu-id="32096-120"><xref:System.EventArgs?displayProperty=nameWithType> types for each operation (of the form <`operationName`>`CompletedEventArgs`) for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="32096-121">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="32096-121">For example:</span></span>  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. <span data-ttu-id="32096-122">Erstellen Sie in der aufrufenden Anwendung eine Rückrufmethode, die aufgerufen wird, wenn der asynchrone Vorgang abgeschlossen ist, wie im folgenden Beispielcode dargestellt.</span><span class="sxs-lookup"><span data-stu-id="32096-122">In the calling application, create a callback method to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. <span data-ttu-id="32096-123">Verwenden Sie vor dem Aufrufen des Vorgangs einen neuen generischen <xref:System.EventHandler%601?displayProperty=nameWithType> vom Typ <, `operationName` > `EventArgs` um die Handlermethode (die im vorherigen Schritt erstellt wurde) dem <-Ereignis hinzuzufügen `operationName` > `Completed` .</span><span class="sxs-lookup"><span data-stu-id="32096-123">Prior to calling the operation, use a new generic <xref:System.EventHandler%601?displayProperty=nameWithType> of type <`operationName`>`EventArgs` to add the handler method (created in the preceding step) to the <`operationName`>`Completed` event.</span></span> <span data-ttu-id="32096-124">Anschließend wird die <- `operationName` > `Async` Methode aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="32096-124">Then call the <`operationName`>`Async` method.</span></span> <span data-ttu-id="32096-125">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="32096-125">For example:</span></span>  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="32096-126">Beispiel</span><span class="sxs-lookup"><span data-stu-id="32096-126">Example</span></span>  
  
> [!NOTE]
> <span data-ttu-id="32096-127">Die Entwurfsrichtlinien für das ereignisbasierte asynchrone Modell besagen, dass in den Fällen, in denen mehr als ein Wert zurückgegeben wird, ein Wert in der `Result`-Eigenschaft und die übrigen Werte in Eigenschaften des <xref:System.EventArgs>-Objekts zurückgegeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="32096-127">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="32096-128">Wenn ein Client Metadaten mithilfe der ereignisbasierten asynchronen Befehlsoptionen importiert und der Vorgang mehr als einen Wert zurückgibt, dann gibt das <xref:System.EventArgs>-Objekt infolgedessen einen Wert in der `Result`-Eigenschaft zurück, und die übrigen Werte werden in Eigenschaften des <xref:System.EventArgs>-Objekts zurückgegeben. Wenn das Nachrichtenobjekt in der `Result`-Eigenschaft und die Rückgabewerte als Eigenschaften dieses Objekts übermittelt werden sollen, verwenden Sie die Befehlsoption `/messageContract`.</span><span class="sxs-lookup"><span data-stu-id="32096-128">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="32096-129">Damit wird eine Signatur generiert, bei der die Antwortnachricht in der `Result`-Eigenschaft des <xref:System.EventArgs>-Objekts zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="32096-129">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="32096-130">Alle internen Rückgabewerte sind dann Eigenschaften des Antwortnachrichtenobjekts.</span><span class="sxs-lookup"><span data-stu-id="32096-130">All internal return values are then properties of the response message object.</span></span>  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="32096-131">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="32096-131">See also</span></span>

- [<span data-ttu-id="32096-132">Vorgehensweise: Implementieren eines asynchronen Dienstvorgangs</span><span class="sxs-lookup"><span data-stu-id="32096-132">How to: Implement an Asynchronous Service Operation</span></span>](../how-to-implement-an-asynchronous-service-operation.md)
