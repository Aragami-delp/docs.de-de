---
title: 'Vorgehensweise: Implementieren eines Suchproxys'
ms.date: 03/30/2017
ms.assetid: 78d70e0a-f6c3-4cfb-a7ca-f66ebddadde0
ms.openlocfilehash: ca7ab2ee434aef7649d71cbfc33273f48020788f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597071"
---
# <a name="how-to-implement-a-discovery-proxy"></a><span data-ttu-id="84a80-102">Vorgehensweise: Implementieren eines Suchproxys</span><span class="sxs-lookup"><span data-stu-id="84a80-102">How to: Implement a Discovery Proxy</span></span>

<span data-ttu-id="84a80-103">In diesem Thema wird erläutert, wie Sie einen Suchproxy implementieren.</span><span class="sxs-lookup"><span data-stu-id="84a80-103">This topic explains how to implement a discovery proxy.</span></span> <span data-ttu-id="84a80-104">Weitere Informationen zur Ermittlungsfunktion in Windows Communication Foundation (WCF) finden Sie unter [Übersicht über die WCF](wcf-discovery-overview.md)-Ermittlung.</span><span class="sxs-lookup"><span data-stu-id="84a80-104">For more information about the discovery feature in Windows Communication Foundation (WCF), see [WCF Discovery Overview](wcf-discovery-overview.md).</span></span> <span data-ttu-id="84a80-105">Sie können einen Suchproxy implementieren, indem Sie eine Klasse erstellen, die die abstrakte <xref:System.ServiceModel.Discovery.DiscoveryProxy>-Klasse erweitert.</span><span class="sxs-lookup"><span data-stu-id="84a80-105">A discovery proxy can be implemented by creating a class that extends the <xref:System.ServiceModel.Discovery.DiscoveryProxy> abstract class.</span></span> <span data-ttu-id="84a80-106">Es gibt eine Reihe von anderen Unterstützungsklassen, die in diesem Beispiel definiert und verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="84a80-106">There are a number of other support classes defined and used in this sample.</span></span> <span data-ttu-id="84a80-107">`OnResolveAsyncResult`, `OnFindAsyncResult`und `AsyncResult`.</span><span class="sxs-lookup"><span data-stu-id="84a80-107">`OnResolveAsyncResult`, `OnFindAsyncResult`, and `AsyncResult`.</span></span> <span data-ttu-id="84a80-108">Diese Klassen implementieren die <xref:System.IAsyncResult>-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="84a80-108">These classes implement the <xref:System.IAsyncResult> interface.</span></span> <span data-ttu-id="84a80-109">Weitere Informationen finden Sie <xref:System.IAsyncResult> unter [System. iasynkresult-Schnittstelle](xref:System.IAsyncResult).</span><span class="sxs-lookup"><span data-stu-id="84a80-109">For more information about <xref:System.IAsyncResult> see [System.IAsyncResult interface](xref:System.IAsyncResult).</span></span>

 <span data-ttu-id="84a80-110">Das Implementieren eines Suchproxys ist in diesem Thema in drei Hauptteile aufgegliedert:</span><span class="sxs-lookup"><span data-stu-id="84a80-110">Implementing a discovery proxy is broken down into three main parts in this topic:</span></span>

- <span data-ttu-id="84a80-111">Definieren einer Klasse, die einen Datenspeicher enthält und die abstrakte <xref:System.ServiceModel.Discovery.DiscoveryProxy>-Klasse erweitert</span><span class="sxs-lookup"><span data-stu-id="84a80-111">Define a class that contains a data store and extends the abstract <xref:System.ServiceModel.Discovery.DiscoveryProxy> class.</span></span>

- <span data-ttu-id="84a80-112">Implementieren der `AsyncResult`-Hilfsklasse</span><span class="sxs-lookup"><span data-stu-id="84a80-112">Implement the helper `AsyncResult` class.</span></span>

- <span data-ttu-id="84a80-113">Hosten des Suchproxys</span><span class="sxs-lookup"><span data-stu-id="84a80-113">Host the Discovery Proxy.</span></span>

### <a name="to-create-a-new-console-application-project"></a><span data-ttu-id="84a80-114">So erstellen Sie ein neues Konsolenanwendungsprojekt</span><span class="sxs-lookup"><span data-stu-id="84a80-114">To create a new console application project</span></span>

1. <span data-ttu-id="84a80-115">Starten Sie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="84a80-115">Start Visual Studio 2012.</span></span>

2. <span data-ttu-id="84a80-116">Erstellen Sie ein neues Konsolenanwendungsprojekt.</span><span class="sxs-lookup"><span data-stu-id="84a80-116">Create a new console application project.</span></span> <span data-ttu-id="84a80-117">Nennen Sie das Projekt `DiscoveryProxy` und die Projektmappe `DiscoveryProxyExample`.</span><span class="sxs-lookup"><span data-stu-id="84a80-117">Name the project `DiscoveryProxy` and the name the solution `DiscoveryProxyExample`.</span></span>

3. <span data-ttu-id="84a80-118">Fügen Sie dem Projekt die folgenden Verweise hinzu.</span><span class="sxs-lookup"><span data-stu-id="84a80-118">Add the following references to the project</span></span>

    1. <span data-ttu-id="84a80-119">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="84a80-119">System.ServiceModel.dll</span></span>

    2. <span data-ttu-id="84a80-120">System.Servicemodel.Discovery.dll</span><span class="sxs-lookup"><span data-stu-id="84a80-120">System.Servicemodel.Discovery.dll</span></span>

    > [!CAUTION]
    > <span data-ttu-id="84a80-121">Stellen Sie sicher, dass Sie für diese Assemblys auf Version 4.0 oder höher verweisen.</span><span class="sxs-lookup"><span data-stu-id="84a80-121">Ensure that you reference version 4.0 or greater of these assemblies.</span></span>

### <a name="to-implement-the-proxydiscoveryservice-class"></a><span data-ttu-id="84a80-122">So implementieren Sie die ProxyDiscoveryService-Klasse</span><span class="sxs-lookup"><span data-stu-id="84a80-122">To implement the ProxyDiscoveryService class</span></span>

1. <span data-ttu-id="84a80-123">Fügen Sie dem Projekt eine neue Codedatei hinzu, und geben Sie dieser den Namen DiscoveryProxy.cs.</span><span class="sxs-lookup"><span data-stu-id="84a80-123">Add a new code file to your project and name it DiscoveryProxy.cs.</span></span>

2. <span data-ttu-id="84a80-124">Fügen Sie der Datei DiscoveryProxy.cs die folgenden `using`-Anweisungen hinzu.</span><span class="sxs-lookup"><span data-stu-id="84a80-124">Add the following `using` statements to DiscoveryProxy.cs.</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    using System.Xml;
    ```

3. <span data-ttu-id="84a80-125">Leiten Sie `DiscoveryProxyService` von <xref:System.ServiceModel.Discovery.DiscoveryProxy> ab.</span><span class="sxs-lookup"><span data-stu-id="84a80-125">Derive the `DiscoveryProxyService` from <xref:System.ServiceModel.Discovery.DiscoveryProxy>.</span></span> <span data-ttu-id="84a80-126">Wenden Sie das `ServiceBehavior`-Attribut auf die Klasse an, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="84a80-126">Apply the `ServiceBehavior` attribute to the class as shown in the following example.</span></span>

    ```csharp
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
    }
    ```

4. <span data-ttu-id="84a80-127">Definieren Sie in der `DiscoveryProxy`-Klasse ein Wörterbuch für die registrierten Dienste.</span><span class="sxs-lookup"><span data-stu-id="84a80-127">Inside the `DiscoveryProxy` class define a dictionary to hold the registered services.</span></span>

    ```csharp
    // Repository to store EndpointDiscoveryMetadata.
    Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;
    ```

5. <span data-ttu-id="84a80-128">Definieren Sie einen Konstruktor, der das Wörterbuch initialisiert.</span><span class="sxs-lookup"><span data-stu-id="84a80-128">Define a constructor that initializes the dictionary.</span></span>

    ```csharp
    public DiscoveryProxyService()
            {
                this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
            }
    ```

### <a name="to-define-the-methods-used-to-update-the-discovery-proxy-cache"></a><span data-ttu-id="84a80-129">So definieren Sie die Methoden, die zum Aktualisieren des Suchproxycaches verwendet werden</span><span class="sxs-lookup"><span data-stu-id="84a80-129">To define the methods used to update the discovery proxy cache</span></span>

1. <span data-ttu-id="84a80-130">Implementieren Sie die `AddOnlineservice`-Methode, um dem Cache Dienste hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="84a80-130">Implement the `AddOnlineservice` method to add services to the cache.</span></span> <span data-ttu-id="84a80-131">Diese Methode wird jedes Mal aufgerufen, wenn der Proxy eine Ankündigungsmeldung empfängt.</span><span class="sxs-lookup"><span data-stu-id="84a80-131">This is called every time the proxy receives an announcement message.</span></span>

    ```csharp
    void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
    {
        lock (this.onlineServices)
        {
            this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;
        }

        PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");
    }
    ```

2. <span data-ttu-id="84a80-132">Implementieren Sie die `RemoveOnlineService`-Methode, die zum Entfernen von Diensten aus dem Cache verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="84a80-132">Implement the `RemoveOnlineService` method that is used to remove services from the cache.</span></span>

    ```csharp
    void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
    {
        if (endpointDiscoveryMetadata != null)
        {
            lock (this.onlineServices)
            {
                this.onlineServices.Remove(endpointDiscoveryMetadata.Address);
            }

            PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");
        }
    }
    ```

3. <span data-ttu-id="84a80-133">Implementieren Sie die `MatchFromOnlineService`-Methoden, die einen Dienst mit einem Dienst im Wörterbuch vergleichen.</span><span class="sxs-lookup"><span data-stu-id="84a80-133">Implement the `MatchFromOnlineService` methods that attempt to match a service with a service in the dictionary.</span></span>

    ```csharp
    void MatchFromOnlineService(FindRequestContext findRequestContext)
    {
        lock (this.onlineServices)
        {
            foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
            {
                if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))
                {
                    findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);
                }
            }
        }
    }
    ```

    ```csharp
    EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)
    {
        EndpointDiscoveryMetadata matchingEndpoint = null;
        lock (this.onlineServices)
        {
            foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
            {
                if (criteria.Address == endpointDiscoveryMetadata.Address)
                {
                    matchingEndpoint = endpointDiscoveryMetadata;
                }
            }
        }
        return matchingEndpoint;
    }
    ```

4. <span data-ttu-id="84a80-134">Implementieren Sie die `PrintDiscoveryMetadata`-Methode, die für Benutzer eine Konsolentextausgabe zu den Aktivitäten des Suchproxys bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="84a80-134">Implement the `PrintDiscoveryMetadata` method that provides the user with console text output of what the discovery proxy is doing.</span></span>

    ```csharp
    void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)
    {
        Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");
        foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)
        {
            Console.WriteLine("** " + contractName.ToString());
            break;
        }
        Console.WriteLine("**** Operation Completed");
    }
    ```

5. <span data-ttu-id="84a80-135">Fügen Sie der Datei DiscoveryProxyService die folgenden AsyncResult-Klassen hinzu.</span><span class="sxs-lookup"><span data-stu-id="84a80-135">Add the following AsyncResult classes to the DiscoveryProxyService.</span></span> <span data-ttu-id="84a80-136">Diese Klassen werden verwendet, um zwischen den einzelnen asynchronen Vorgangsergebnissen zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="84a80-136">These classes are used to differentiate between the different asynchronous operation results.</span></span>

    ```csharp
    sealed class OnOnlineAnnouncementAsyncResult : AsyncResult
    {
        public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.Complete(true);
        }

        public static void End(IAsyncResult result)
        {
            AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);
        }
    }

    sealed class OnOfflineAnnouncementAsyncResult : AsyncResult
    {
        public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.Complete(true);
        }

        public static void End(IAsyncResult result)
        {
            AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);
        }
    }

    sealed class OnFindAsyncResult : AsyncResult
    {
        public OnFindAsyncResult(AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.Complete(true);
        }

        public static void End(IAsyncResult result)
        {
            AsyncResult.End<OnFindAsyncResult>(result);
        }
    }

    sealed class OnResolveAsyncResult : AsyncResult
    {
        EndpointDiscoveryMetadata matchingEndpoint;

        public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.matchingEndpoint = matchingEndpoint;
            this.Complete(true);
        }

        public static EndpointDiscoveryMetadata End(IAsyncResult result)
        {
            OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);
            return thisPtr.matchingEndpoint;
        }
    }
    ```

### <a name="to-define-the-methods-that-implement-the-discovery-proxy-functionality"></a><span data-ttu-id="84a80-137">So definieren Sie die Methoden, die die Suchproxyfunktionalität implementieren</span><span class="sxs-lookup"><span data-stu-id="84a80-137">To define the methods that implement the discovery proxy functionality</span></span>

1. <span data-ttu-id="84a80-138">Überschreiben Sie die <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> -Methode.</span><span class="sxs-lookup"><span data-stu-id="84a80-138">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="84a80-139">Diese Methode wird aufgerufen, wenn der Suchproxy eine Onlineankündigungsmeldung empfängt.</span><span class="sxs-lookup"><span data-stu-id="84a80-139">This method is called when the discovery proxy receives an online announcement message.</span></span>

    ```csharp
    // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
    protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
    {
        this.AddOnlineService(endpointDiscoveryMetadata);
        return new OnOnlineAnnouncementAsyncResult(callback, state);
    }
    ```

2. <span data-ttu-id="84a80-140">Überschreiben Sie die <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> -Methode.</span><span class="sxs-lookup"><span data-stu-id="84a80-140">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="84a80-141">Diese Methode wird aufgerufen, wenn der Suchproxy die Verarbeitung einer Ankündigungsmeldung beendet.</span><span class="sxs-lookup"><span data-stu-id="84a80-141">This method is called when the discovery proxy finishes processing an announcement message.</span></span>

    ```csharp
    protected override void OnEndOnlineAnnouncement(IAsyncResult result)
    {
        OnOnlineAnnouncementAsyncResult.End(result);
    }
    ```

3. <span data-ttu-id="84a80-142">Überschreiben Sie die <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> -Methode.</span><span class="sxs-lookup"><span data-stu-id="84a80-142">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="84a80-143">Diese Methode wird aufgerufen, wenn der Suchproxy eine Offlineankündigungsmeldung empfängt.</span><span class="sxs-lookup"><span data-stu-id="84a80-143">This method is called with the discovery proxy receives an offline announcement message.</span></span>

    ```csharp
    // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
    protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
    {
        this.RemoveOnlineService(endpointDiscoveryMetadata);
        return new OnOfflineAnnouncementAsyncResult(callback, state);
    }
    ```

4. <span data-ttu-id="84a80-144">Überschreiben Sie die <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> -Methode.</span><span class="sxs-lookup"><span data-stu-id="84a80-144">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="84a80-145">Diese Methode wird aufgerufen, wenn der Suchproxy die Verarbeitung einer Offlineankündigungsmeldung beendet.</span><span class="sxs-lookup"><span data-stu-id="84a80-145">This method is called when the discovery proxy finishes processing an offline announcement message.</span></span>

    ```csharp
    protected override void OnEndOfflineAnnouncement(IAsyncResult result)
    {
        OnOfflineAnnouncementAsyncResult.End(result);
    }
    ```

5. <span data-ttu-id="84a80-146">Überschreiben Sie die <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> -Methode.</span><span class="sxs-lookup"><span data-stu-id="84a80-146">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="84a80-147">Diese Methode wird aufgerufen, wenn der Suchproxy eine Suchanforderung empfängt.</span><span class="sxs-lookup"><span data-stu-id="84a80-147">This method is called when the discovery proxy receives a find request.</span></span>

    ```csharp
    // OnBeginFind method is called when a Probe request message is received by the Proxy
    protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)
    {
        this.MatchFromOnlineService(findRequestContext);
        return new OnFindAsyncResult(callback, state);
    }
    protected override IAsyncResult OnBeginFind(FindRequest findRequest, AsyncCallback callback, object state)
    {
        Collection<EndpointDiscoveryMetadata> matchingEndpoints = MatchFromCache(findRequest.Criteria);
        return new OnFindAsyncResult(
                    matchingEndpoints,
                    callback,
                    state);
    }
    ```

6. <span data-ttu-id="84a80-148">Überschreiben Sie die <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> -Methode.</span><span class="sxs-lookup"><span data-stu-id="84a80-148">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="84a80-149">Diese Methode wird aufgerufen, wenn der Suchproxy die Verarbeitung einer Suchanforderung beendet.</span><span class="sxs-lookup"><span data-stu-id="84a80-149">This method is called when the discovery proxy finishes processing a find request.</span></span>

    ```csharp
    protected override void OnEndFind(IAsyncResult result)
    {
        OnFindAsyncResult.End(result);
    }
    ```

7. <span data-ttu-id="84a80-150">Überschreiben Sie die <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> -Methode.</span><span class="sxs-lookup"><span data-stu-id="84a80-150">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="84a80-151">Diese Methode wird aufgerufen, wenn der Suchproxy eine Auflösungsnachricht empfängt.</span><span class="sxs-lookup"><span data-stu-id="84a80-151">This method is called when the discovery proxy receives a resolve message.</span></span>

    ```csharp
    // OnBeginFind method is called when a Resolve request message is received by the Proxy
    protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)
    {
        return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);
    }
    protected override IAsyncResult OnBeginResolve(ResolveRequest resolveRequest, AsyncCallback callback, object state)
    {
        return new OnResolveAsyncResult(
            this.proxy.MatchFromOnlineService(resolveRequest.Criteria),
            callback,
            state);
    }
    ```

8. <span data-ttu-id="84a80-152">Überschreiben Sie die <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> -Methode.</span><span class="sxs-lookup"><span data-stu-id="84a80-152">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="84a80-153">Diese Methode wird aufgerufen, wenn der Suchproxy die Verarbeitung einer Auflösungsnachricht beendet.</span><span class="sxs-lookup"><span data-stu-id="84a80-153">This method is called when the discovery proxy finishes processing a resolve message.</span></span>

    ```csharp
    protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
    {
        return OnResolveAsyncResult.End(result);
    }
    ```

<span data-ttu-id="84a80-154">Die OnBegin/</span><span class="sxs-lookup"><span data-stu-id="84a80-154">The OnBegin..</span></span> <span data-ttu-id="84a80-155">/ OnEnd.</span><span class="sxs-lookup"><span data-stu-id="84a80-155">/ OnEnd..</span></span> <span data-ttu-id="84a80-156">-Methoden stellen die Logik für die nachfolgenden Suchvorgänge bereit.</span><span class="sxs-lookup"><span data-stu-id="84a80-156">methods provide the logic for the subsequent discovery operations.</span></span> <span data-ttu-id="84a80-157">Die Methoden <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> und <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> implementieren z. B. die Suchlogik für den Suchproxy.</span><span class="sxs-lookup"><span data-stu-id="84a80-157">For example the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> and <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> methods implement the find logic for discovery proxy.</span></span> <span data-ttu-id="84a80-158">Wenn der Suchproxy eine Überprüfungsmeldung empfängt, werden diese Methoden ausgeführt, um eine Antwort an den Client zurückzusenden.</span><span class="sxs-lookup"><span data-stu-id="84a80-158">When the discovery proxy receives a probe message these methods are executed to send a response back to the client.</span></span> <span data-ttu-id="84a80-159">Sie können die Suchlogik nach Belieben ändern. Beispielsweise können Sie als Teil des Suchvorgangs eine benutzerdefinierte Bereichsübereinstimmung integrieren, die auf Algorithmen oder einer anwendungsspezifischen Analyse der XML-Metadaten basiert.</span><span class="sxs-lookup"><span data-stu-id="84a80-159">You may modify the find logic as you wish, for example you can incorporate custom scope matching by algorithms or application specific XML metadata parsing as part of your find operation.</span></span>

### <a name="to-implement-the-asyncresult-class"></a><span data-ttu-id="84a80-160">So implementieren Sie die AsyncResult-Klasse</span><span class="sxs-lookup"><span data-stu-id="84a80-160">To implement the AsyncResult class</span></span>

1. <span data-ttu-id="84a80-161">Definieren Sie die abstrakte Basisklasse AsyncResult, die zum Ableiten der verschiedenen AsyncResult-Klassen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="84a80-161">Define the abstract base class AsyncResult which is used to derive the various async result classes.</span></span>

2. <span data-ttu-id="84a80-162">Erstellen Sie eine neue Codedatei mit dem Namen AsyncResult.cs.</span><span class="sxs-lookup"><span data-stu-id="84a80-162">Create a new code file called AsyncResult.cs.</span></span>

3. <span data-ttu-id="84a80-163">Fügen Sie der Datei AsyncResult.cs die folgenden `using`-Anweisungen hinzu.</span><span class="sxs-lookup"><span data-stu-id="84a80-163">Add the following `using` statements to AsyncResult.cs.</span></span>

    ```csharp
    using System;
    using System.Threading;
    ```

4. <span data-ttu-id="84a80-164">Fügen Sie die folgende AsyncResult-Klasse hinzu.</span><span class="sxs-lookup"><span data-stu-id="84a80-164">Add the following AsyncResult class.</span></span>

    ```csharp
    abstract class AsyncResult : IAsyncResult
    {
        AsyncCallback callback;
        bool completedSynchronously;
        bool endCalled;
        Exception exception;
        bool isCompleted;
        ManualResetEvent manualResetEvent;
        object state;
        object thisLock;

        protected AsyncResult(AsyncCallback callback, object state)
        {
            this.callback = callback;
            this.state = state;
            this.thisLock = new object();
        }

        public object AsyncState
        {
            get
            {
                return state;
            }
        }

        public WaitHandle AsyncWaitHandle
        {
            get
            {
                if (manualResetEvent != null)
                {
                    return manualResetEvent;
                }
                lock (ThisLock)
                {
                    manualResetEvent ??= new ManualResetEvent(isCompleted);
                }
                return manualResetEvent;
            }
        }

        public bool CompletedSynchronously
        {
            get
            {
                return completedSynchronously;
            }
        }

        public bool IsCompleted
        {
            get
            {
                return isCompleted;
            }
        }

        object ThisLock
        {
            get
            {
                return this.thisLock;
            }
        }

        protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)
            where TAsyncResult : AsyncResult
        {
            if (result == null)
            {
                throw new ArgumentNullException("result");
            }

            TAsyncResult asyncResult = result as TAsyncResult;

            if (asyncResult == null)
            {
                throw new ArgumentException("Invalid async result.", "result");
            }

            if (asyncResult.endCalled)
            {
                throw new InvalidOperationException("Async object already ended.");
            }

            asyncResult.endCalled = true;

            if (!asyncResult.isCompleted)
            {
                asyncResult.AsyncWaitHandle.WaitOne();
            }

            if (asyncResult.manualResetEvent != null)
            {
                asyncResult.manualResetEvent.Close();
            }

            if (asyncResult.exception != null)
            {
                throw asyncResult.exception;
            }

            return asyncResult;
        }

        protected void Complete(bool completedSynchronously)
        {
            if (isCompleted)
            {
                throw new InvalidOperationException("This async result is already completed.");
            }

            this.completedSynchronously = completedSynchronously;

            if (completedSynchronously)
            {
                this.isCompleted = true;
            }
            else
            {
                lock (ThisLock)
                {
                    this.isCompleted = true;
                    if (this.manualResetEvent != null)
                    {
                        this.manualResetEvent.Set();
                    }
                }
            }

            if (callback != null)
            {
                callback(this);
            }
        }

        protected void Complete(bool completedSynchronously, Exception exception)
        {
            this.exception = exception;
            Complete(completedSynchronously);
        }
    }
    ```

### <a name="to-host-the-discoveryproxy"></a><span data-ttu-id="84a80-165">So hosten Sie den DiscoveryProxy</span><span class="sxs-lookup"><span data-stu-id="84a80-165">To host the DiscoveryProxy</span></span>

1. <span data-ttu-id="84a80-166">Öffnen Sie die Datei Program.cs im Projekt DiscoveryProxyExample.</span><span class="sxs-lookup"><span data-stu-id="84a80-166">Open the Program.cs file in the DiscoveryProxyExample project.</span></span>

2. <span data-ttu-id="84a80-167">Fügen Sie die folgenden `using`-Anweisungen hinzu:</span><span class="sxs-lookup"><span data-stu-id="84a80-167">Add the following `using` statements.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    ```

3. <span data-ttu-id="84a80-168">Fügen Sie in der `Main()`-Methode den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="84a80-168">Within the `Main()` method, add the following code.</span></span> <span data-ttu-id="84a80-169">Dadurch wird eine Instanz der `DiscoveryProxy`-Klasse erstellt.</span><span class="sxs-lookup"><span data-stu-id="84a80-169">This creates an instance of the `DiscoveryProxy` class.</span></span>

    ```csharp
    Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
    Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

    // Host the DiscoveryProxy service
    ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());
    ```

4. <span data-ttu-id="84a80-170">Fügen Sie danach den folgenden Code hinzu, um einen Suchendpunkt und einen Ankündigungsendpunkt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="84a80-170">Next add the following code to add a discovery endpoint and an announcement endpoint.</span></span>

    ```csharp
    try
    {
        // Add DiscoveryEndpoint to receive Probe and Resolve messages
        DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));
        discoveryEndpoint.IsSystemEndpoint = false;

        // Add AnnouncementEndpoint to receive Hello and Bye announcement messages
        AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));

        proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);
        proxyServiceHost.AddServiceEndpoint(announcementEndpoint);

        proxyServiceHost.Open();

        Console.WriteLine("Proxy Service started.");
        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate the service.");
        Console.WriteLine();
        Console.ReadLine();

        proxyServiceHost.Close();
    }
    catch (CommunicationException e)
    {
        Console.WriteLine(e.Message);
    }
    catch (TimeoutException e)
    {
        Console.WriteLine(e.Message);
    }

    if (proxyServiceHost.State != CommunicationState.Closed)
    {
        Console.WriteLine("Aborting the service...");
        proxyServiceHost.Abort();
    }
    ```

<span data-ttu-id="84a80-171">Sie haben die Implementierung des Suchproxys abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="84a80-171">You have completed implementing the discovery proxy.</span></span> <span data-ttu-id="84a80-172">Weitere Informationen finden Sie unter Gewusst [wie: Implementieren eines erkennbaren Dienstanbieter, der beim suchproxy registriert](discoverable-service-that-registers-with-the-discovery-proxy.md)wird.</span><span class="sxs-lookup"><span data-stu-id="84a80-172">Continue on to [How to: Implement a Discoverable Service that Registers with the Discovery Proxy](discoverable-service-that-registers-with-the-discovery-proxy.md).</span></span>

## <a name="example"></a><span data-ttu-id="84a80-173">Beispiel</span><span class="sxs-lookup"><span data-stu-id="84a80-173">Example</span></span>

<span data-ttu-id="84a80-174">Dies ist die vollständige Codeauflistung für dieses Thema.</span><span class="sxs-lookup"><span data-stu-id="84a80-174">This is the full listing of the code used in this topic.</span></span>

```csharp
// DiscoveryProxy.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.Collections.Generic;
using System.ServiceModel;
using System.ServiceModel.Discovery;
using System.Xml;

namespace Microsoft.Samples.Discovery
{
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
        // Repository to store EndpointDiscoveryMetadata. A database or a flat file could also be used instead.
        Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;

        public DiscoveryProxyService()
        {
            this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
        }

        // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
        protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
        {
            this.AddOnlineService(endpointDiscoveryMetadata);
            return new OnOnlineAnnouncementAsyncResult(callback, state);
        }

        protected override void OnEndOnlineAnnouncement(IAsyncResult result)
        {
            OnOnlineAnnouncementAsyncResult.End(result);
        }

        // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
        protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
        {
            this.RemoveOnlineService(endpointDiscoveryMetadata);
            return new OnOfflineAnnouncementAsyncResult(callback, state);
        }

        protected override void OnEndOfflineAnnouncement(IAsyncResult result)
        {
            OnOfflineAnnouncementAsyncResult.End(result);
        }

        // OnBeginFind method is called when a Probe request message is received by the Proxy
        protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)
        {
            this.MatchFromOnlineService(findRequestContext);
            return new OnFindAsyncResult(callback, state);
        }

        protected override void OnEndFind(IAsyncResult result)
        {
            OnFindAsyncResult.End(result);
        }

        // OnBeginFind method is called when a Resolve request message is received by the Proxy
        protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)
        {
            return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);
        }

        protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
        {
            return OnResolveAsyncResult.End(result);
        }

        // The following are helper methods required by the Proxy implementation
        void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
        {
            lock (this.onlineServices)
            {
                this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;
            }

            PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");
        }

        void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
        {
            if (endpointDiscoveryMetadata != null)
            {
                lock (this.onlineServices)
                {
                    this.onlineServices.Remove(endpointDiscoveryMetadata.Address);
                }

                PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");
            }
        }

        void MatchFromOnlineService(FindRequestContext findRequestContext)
        {
            lock (this.onlineServices)
            {
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                {
                    if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))
                    {
                        findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);
                    }
                }
            }
        }

        EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)
        {
            EndpointDiscoveryMetadata matchingEndpoint = null;
            lock (this.onlineServices)
            {
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                {
                    if (criteria.Address == endpointDiscoveryMetadata.Address)
                    {
                        matchingEndpoint = endpointDiscoveryMetadata;
                    }
                }
            }
            return matchingEndpoint;
        }

        void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)
        {
            Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");
            foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)
            {
                Console.WriteLine("** " + contractName.ToString());
                break;
            }
            Console.WriteLine("**** Operation Completed");
        }

        sealed class OnOnlineAnnouncementAsyncResult : AsyncResult
        {
            public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);
            }
        }

        sealed class OnOfflineAnnouncementAsyncResult : AsyncResult
        {
            public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);
            }
        }

        sealed class OnFindAsyncResult : AsyncResult
        {
            public OnFindAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnFindAsyncResult>(result);
            }
        }

        sealed class OnResolveAsyncResult : AsyncResult
        {
            EndpointDiscoveryMetadata matchingEndpoint;

            public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.matchingEndpoint = matchingEndpoint;
                this.Complete(true);
            }

            public static EndpointDiscoveryMetadata End(IAsyncResult result)
            {
                OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);
                return thisPtr.matchingEndpoint;
            }
        }
    }
}
```

```csharp
// AsyncResult.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.Threading;

namespace Microsoft.Samples.Discovery
{
    abstract class AsyncResult : IAsyncResult
    {
        AsyncCallback callback;
        bool completedSynchronously;
        bool endCalled;
        Exception exception;
        bool isCompleted;
        ManualResetEvent manualResetEvent;
        object state;
        object thisLock;

        protected AsyncResult(AsyncCallback callback, object state)
        {
            this.callback = callback;
            this.state = state;
            this.thisLock = new object();
        }

        public object AsyncState
        {
            get
            {
                return state;
            }
        }

        public WaitHandle AsyncWaitHandle
        {
            get
            {
                if (manualResetEvent != null)
                {
                    return manualResetEvent;
                }
                lock (ThisLock)
                {
                    manualResetEvent ??= new ManualResetEvent(isCompleted);
                }
                return manualResetEvent;
            }
        }

        public bool CompletedSynchronously
        {
            get
            {
                return completedSynchronously;
            }
        }

        public bool IsCompleted
        {
            get
            {
                return isCompleted;
            }
        }

        object ThisLock
        {
            get
            {
                return this.thisLock;
            }
        }

        protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)
            where TAsyncResult : AsyncResult
        {
            if (result == null)
            {
                throw new ArgumentNullException("result");
            }

            TAsyncResult asyncResult = result as TAsyncResult;

            if (asyncResult == null)
            {
                throw new ArgumentException("Invalid async result.", "result");
            }

            if (asyncResult.endCalled)
            {
                throw new InvalidOperationException("Async object already ended.");
            }

            asyncResult.endCalled = true;

            if (!asyncResult.isCompleted)
            {
                asyncResult.AsyncWaitHandle.WaitOne();
            }

            if (asyncResult.manualResetEvent != null)
            {
                asyncResult.manualResetEvent.Close();
            }

            if (asyncResult.exception != null)
            {
                throw asyncResult.exception;
            }

            return asyncResult;
        }

        protected void Complete(bool completedSynchronously)
        {
            if (isCompleted)
            {
                throw new InvalidOperationException("This async result is already completed.");
            }

            this.completedSynchronously = completedSynchronously;

            if (completedSynchronously)
            {
                this.isCompleted = true;
            }
            else
            {
                lock (ThisLock)
                {
                    this.isCompleted = true;
                    if (this.manualResetEvent != null)
                    {
                        this.manualResetEvent.Set();
                    }
                }
            }

            if (callback != null)
            {
                callback(this);
            }
        }

        protected void Complete(bool completedSynchronously, Exception exception)
        {
            this.exception = exception;
            Complete(completedSynchronously);
        }
    }
}
```

```csharp
// program.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;
using System.ServiceModel.Discovery;

namespace Microsoft.Samples.Discovery
{
    class Program
    {
        public static void Main()
        {
            Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
            Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

            // Host the DiscoveryProxy service
            ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());

            try
            {
                // Add DiscoveryEndpoint to receive Probe and Resolve messages
                DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));
                discoveryEndpoint.IsSystemEndpoint = false;

                // Add AnnouncementEndpoint to receive Hello and Bye announcement messages
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));

                proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);
                proxyServiceHost.AddServiceEndpoint(announcementEndpoint);

                proxyServiceHost.Open();

                Console.WriteLine("Proxy Service started.");
                Console.WriteLine();
                Console.WriteLine("Press <ENTER> to terminate the service.");
                Console.WriteLine();
                Console.ReadLine();

                proxyServiceHost.Close();
            }
            catch (CommunicationException e)
            {
                Console.WriteLine(e.Message);
            }
            catch (TimeoutException e)
            {
                Console.WriteLine(e.Message);
            }

            if (proxyServiceHost.State != CommunicationState.Closed)
            {
                Console.WriteLine("Aborting the service...");
                proxyServiceHost.Abort();
            }
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="84a80-175">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="84a80-175">See also</span></span>

- [<span data-ttu-id="84a80-176">Übersicht über die WCF-Suche</span><span class="sxs-lookup"><span data-stu-id="84a80-176">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="84a80-177">Vorgehensweise: Implementieren eines ermittelbaren Diensts, der beim Suchproxy registriert ist</span><span class="sxs-lookup"><span data-stu-id="84a80-177">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="84a80-178">Vorgehensweise: Implementieren einer Clientanwendung, die den Suchproxy zum Suchen nach einem Dienst verwendet</span><span class="sxs-lookup"><span data-stu-id="84a80-178">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)
- [<span data-ttu-id="84a80-179">Vorgehensweise: Testen des Suchproxys</span><span class="sxs-lookup"><span data-stu-id="84a80-179">How to: Test the Discovery Proxy</span></span>](how-to-test-the-discovery-proxy.md)
