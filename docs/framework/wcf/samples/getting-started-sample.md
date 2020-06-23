---
title: Beispiel 'Erste Schritte'
description: Erfahren Sie, wie Sie einen typischen Dienst und einen typischen Client mithilfe von WCF implementieren. Es dient als Grundlage für alle anderen grundlegenden Technologiebeispiele.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
ms.openlocfilehash: b23be1b33f227154b916429c063ec4106229bb3c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246232"
---
# <a name="getting-started-sample"></a><span data-ttu-id="22303-104">Beispiel 'Erste Schritte'</span><span class="sxs-lookup"><span data-stu-id="22303-104">Getting Started Sample</span></span>

<span data-ttu-id="22303-105">Das Beispiel "Getting Started" veranschaulicht, wie ein typischer Dienst und ein typischer Client mithilfe von Windows Communication Foundation (WCF) implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="22303-105">The Getting Started sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="22303-106">Es dient als Grundlage für alle anderen grundlegenden Technologiebeispiele.</span><span class="sxs-lookup"><span data-stu-id="22303-106">This sample is the basis for all other basic technology samples.</span></span>

> [!NOTE]
> <span data-ttu-id="22303-107">Die Setupprozedur und die Buildanweisungen für dieses Beispiel befinden sich am Ende dieses Themas.</span><span class="sxs-lookup"><span data-stu-id="22303-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="22303-108">Die Beispiele sind möglicherweise bereits auf dem Computer installiert.</span><span class="sxs-lookup"><span data-stu-id="22303-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="22303-109">Suchen Sie nach dem folgenden Verzeichnis (Standardverzeichnis), bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="22303-109">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="22303-110">Wenn dieses Verzeichnis nicht vorhanden ist, wechseln Sie zu [Windows Communication Foundation (WCF) und Windows Workflow Foundation (WF)-Beispiele für .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , um alle Windows Communication Foundation (WCF) und Beispiele herunterzuladen [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="22303-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="22303-111">Dieses Beispiel befindet sich im folgenden Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="22303-111">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\GettingStarted\GettingStarted`

<span data-ttu-id="22303-112">Der Dienst beschreibt die Vorgänge, die er in einem Dienstvertrag ausführt, den er öffentlich als Metadaten verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="22303-112">The service describes the operations it performs in a service contract that it exposes publicly as metadata.</span></span> <span data-ttu-id="22303-113">Der Dienst enthält auch den Code, um die Vorgänge zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="22303-113">The service also contains the code to implement the operations.</span></span>

<span data-ttu-id="22303-114">Der Client enthält eine Definition des Dienstvertrags und eine Proxyklasse zum Zugreifen auf den Dienst.</span><span class="sxs-lookup"><span data-stu-id="22303-114">The client contains a definition of the service contract and a proxy class for accessing the service.</span></span> <span data-ttu-id="22303-115">Der Proxy Code wird aus den Dienst Metadaten mit dem Service [Model Metadata Utility-Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)generiert.</span><span class="sxs-lookup"><span data-stu-id="22303-115">The proxy code is generated from the service metadata using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

<span data-ttu-id="22303-116">Unter Windows Vista wird der-Dienst im Windows-Aktivierungs Dienst (was) gehostet.</span><span class="sxs-lookup"><span data-stu-id="22303-116">On Windows Vista, the service is hosted in the Windows Activation Service (WAS).</span></span> <span data-ttu-id="22303-117">Unter Windows XP und Windows Server 2003 wird Sie von Internetinformationsdienste (IIS) und ASP.net gehostet.</span><span class="sxs-lookup"><span data-stu-id="22303-117">On Windows XP and Windows Server 2003, it is hosted by Internet Information Services (IIS) and ASP.NET.</span></span> <span data-ttu-id="22303-118">Durch das Hosten eines Diensts in IIS oder WAS kann der Dienst beim ersten Zugriff automatisch aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="22303-118">Hosting a service in IIS or WAS allows the service to be activated automatically when it is accessed for the first time.</span></span>

> [!NOTE]
> <span data-ttu-id="22303-119">Wenn Sie lieber mit einem Beispiel beginnen möchten, das den Dienst in einer Konsolenanwendung anstelle von IIS hostet, finden Sie weitere Informationen unter [Self-Host-](self-host.md) Beispiel.</span><span class="sxs-lookup"><span data-stu-id="22303-119">If you would prefer to get started with a sample that hosts the service in a console application instead of IIS, see the [Self-Host](self-host.md) sample.</span></span>

<span data-ttu-id="22303-120">Der Dienst und der Client legen in den Einstellungen der Konfigurationsdatei Zugriffsdetails fest, die zum Zeitpunkt der Bereitstellung Flexibilität bieten.</span><span class="sxs-lookup"><span data-stu-id="22303-120">The service and client specify access details in configuration file settings, which provide flexibility at the time of deployment.</span></span> <span data-ttu-id="22303-121">Dazu gehört eine Endpunktdefinition, die eine Adresse, eine Bindung und einen Vertrag angibt.</span><span class="sxs-lookup"><span data-stu-id="22303-121">This includes an endpoint definition that specifies an address, binding, and contract.</span></span> <span data-ttu-id="22303-122">Die Bindung gibt Transport- und Sicherheitsdetails für den Zugriff auf den Dienst an.</span><span class="sxs-lookup"><span data-stu-id="22303-122">The binding specifies transport and security details for how the service is to be accessed.</span></span>

<span data-ttu-id="22303-123">Der Dienst konfiguriert ein Laufzeitverhalten, um seine Metadaten zu veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="22303-123">The service configures a run-time behavior to publish its metadata.</span></span>

<span data-ttu-id="22303-124">Der Dienst implementiert einen Vertrag, der ein Anforderungs-Antwort-Kommunikationsmuster definiert.</span><span class="sxs-lookup"><span data-stu-id="22303-124">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="22303-125">Der Vertrag wird von der `ICalculator`-Schnittstelle definiert, die mathematische Operationen (Addieren, Subtrahieren, Multiplizieren und Dividieren) verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="22303-125">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="22303-126">Der Client stellt Anforderungen an eine angegebene mathematische Operation, und der Dienst antwortet mit dem Ergebnis.</span><span class="sxs-lookup"><span data-stu-id="22303-126">The client makes requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="22303-127">Der Dienst implementiert einen `ICalculator`-Vertrag, der im folgenden Code definiert wird.</span><span class="sxs-lookup"><span data-stu-id="22303-127">The service implements an `ICalculator` contract that is defined in the following code.</span></span>

```vb
' Define a service contract.
    <ServiceContract(Namespace:="http://Microsoft.Samples.GettingStarted")>
     Public Interface ICalculator
        <OperationContract()>
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
    End Interface
```

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="22303-128">Die Dienstimplementierung berechnet das entsprechende Ergebnis und gibt es zurück, wie im folgenden Beispielcode dargestellt.</span><span class="sxs-lookup"><span data-stu-id="22303-128">The service implementation calculates and returns the appropriate result, as shown in the following example code.</span></span>

```vb
' Service class which implements the service contract.
Public Class CalculatorService
Implements ICalculator
Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
Return n1 + n2
End Function

Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
Return n1 - n2
End Function

Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
Return n1 * n2
End Function

Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
Return n1 / n2
End Function
End Class
```

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

<span data-ttu-id="22303-129">Der Dienst macht einen Endpunkt zur Kommunikation mit dem Dienst verfügbar. Dieser Endpunkt wird mit einer Konfigurationsdatei (Web.config) definiert, wie in der folgenden Beispielkonfiguration gezeigt.</span><span class="sxs-lookup"><span data-stu-id="22303-129">The service exposes an endpoint for communicating with the service, defined using a configuration file (Web.config), as shown in the following sample configuration.</span></span>

```xaml
<services>
    <service
        name="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
        <!-- ICalculator is exposed at the base address provided by
         host: http://localhost/servicemodelsamples/service.svc.  -->
       <endpoint address=""
              binding="wsHttpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
       ...
    </service>
</services>
```

<span data-ttu-id="22303-130">Der Dienst macht den Endpunkt bei der vom IIS-Host oder WAS-Host bereitgestellten Basisadresse verfügbar.</span><span class="sxs-lookup"><span data-stu-id="22303-130">The service exposes the endpoint at the base address provided by the IIS or WAS host.</span></span> <span data-ttu-id="22303-131">Die Bindung ist mit einer standardmäßigen <xref:System.ServiceModel.WSHttpBinding> konfiguriert, die HTTP-Kommunikation und standardmäßige Webdienstprotokolle für die Adressierung und Sicherheit bietet.</span><span class="sxs-lookup"><span data-stu-id="22303-131">The binding is configured with a standard <xref:System.ServiceModel.WSHttpBinding>, which provides HTTP communication and standard Web service protocols for addressing and security.</span></span> <span data-ttu-id="22303-132">Bei dem Vertrag handelt es sich um den vom Dienst implementierten `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="22303-132">The contract is the `ICalculator` implemented by the service.</span></span>

<span data-ttu-id="22303-133">Wie konfiguriert, kann `http://localhost/servicemodelsamples/service.svc` von einem Client auf dem gleichen Computer auf den Dienst zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="22303-133">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="22303-134">Bei Clients auf Remotecomputern muss für den Dienstzugriff anstelle von localhost ein vollqualifizierter Domänenname angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="22303-134">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span>

<span data-ttu-id="22303-135">Standardmäßig macht das Framework keine Metadaten verfügbar.</span><span class="sxs-lookup"><span data-stu-id="22303-135">The framework does not expose metadata by default.</span></span> <span data-ttu-id="22303-136">Daher wird der-Dienst eingeschaltet und macht <xref:System.ServiceModel.Description.ServiceMetadataBehavior> einen MEX-Endpunkt (Metadata Exchange) unter verfügbar `http://localhost/servicemodelsamples/service.svc/mex` .</span><span class="sxs-lookup"><span data-stu-id="22303-136">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> and exposes a metadata exchange (MEX) endpoint at `http://localhost/servicemodelsamples/service.svc/mex`.</span></span> <span data-ttu-id="22303-137">Dies wird in der folgenden Konfiguration veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="22303-137">The following configuration demonstrates this.</span></span>

```xaml
<system.serviceModel>
  <services>
    <service
        name="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
      ...
      <!-- the mex endpoint is exposed at
       http://localhost/servicemodelsamples/service.svc/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>

  <!--For debugging purposes set the includeExceptionDetailInFaults
   attribute to true-->
  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="True"/>
        <serviceDebug includeExceptionDetailInFaults="False" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```

<span data-ttu-id="22303-138">Der Client kommuniziert mithilfe eines angegebenen Vertrags Typs mithilfe einer Client Klasse, die vom [Service Model Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)generiert wird.</span><span class="sxs-lookup"><span data-stu-id="22303-138">The client communicates using a given contract type by using a client class that is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="22303-139">Dieser generierte Client ist in der Datei "generatedClient.cs" oder der Datei "generatedClient.vb" enthalten.</span><span class="sxs-lookup"><span data-stu-id="22303-139">This generated client is contained in the file generatedClient.cs or generatedClient.vb.</span></span> <span data-ttu-id="22303-140">Dieses Hilfsprogramm ruft Metadaten für einen angegebenen Dienst ab und generiert einen Client, den die Clientanwendung zur Kommunikation mithilfe eines angegebenen Vertragstyps verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="22303-140">This utility retrieves metadata for a given service and generates a client for use by the client application to communicate using a given contract type.</span></span> <span data-ttu-id="22303-141">Der gehostete Dienst muss zur Generierung des Clientcodes verfügbar sein, da der Dienst zum Abrufen der aktualisierten Metadaten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="22303-141">The hosted service must be available to generate the client code, because the service is used to retrieve the updated metadata.</span></span>

 <span data-ttu-id="22303-142">Führen Sie den folgenden Befehl an der SDK-Eingabeaufforderung im Clientverzeichnis aus, um den typisierten Proxy zu generieren:</span><span class="sxs-lookup"><span data-stu-id="22303-142">Run the following command from the SDK command prompt in the client directory to generate the typed proxy:</span></span>

```console
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
```

<span data-ttu-id="22303-143">Geben Sie zum Generieren des Clients in Visual Basic die folgende Zeichenfolge an der SDK-Eingabeaufforderung ein:</span><span class="sxs-lookup"><span data-stu-id="22303-143">To generate client in Visual Basic type the following from the SDK command prompt:</span></span>

`Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`

<span data-ttu-id="22303-144">Wenn der generierte Client verwendet wird, kann der Client auf einen bestimmten Endpunkt zugreifen, indem er die entsprechende Adresse und Bindung konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="22303-144">By using the generated client, the client can access a given service endpoint by configuring the appropriate address and binding.</span></span> <span data-ttu-id="22303-145">Wie auch der Dienst gibt der Client den Endpunkt, mit dem er kommunizieren möchte, mithilfe einer Konfigurationsdatei (App.config) an.</span><span class="sxs-lookup"><span data-stu-id="22303-145">Like the service, the client uses a configuration file (App.config) to specify the endpoint with which it wants to communicate.</span></span> <span data-ttu-id="22303-146">Die Clientendpunktkonfiguration besteht aus einer absoluten Adresse für den Dienstendpunkt, der Bindung und dem Vertrag, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="22303-146">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract, as shown in the following example.</span></span>

```xaml
<client>
     <endpoint
         address="http://localhost/servicemodelsamples/service.svc"
         binding="wsHttpBinding"
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />
</client>
```

<span data-ttu-id="22303-147">Die Clientimplementierung instanziiert den Client und verwendet die typisierte Schnittstelle, um die Kommunikation mit dem Dienst zu beginnen, wie im folgenden Codebeispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="22303-147">The client implementation instantiates the client and uses the typed interface to begin communicating with the service, as shown in the following example code.</span></span>

```vb
' Create a client
Dim client As New CalculatorClient()

' Call the Add service operation.
            Dim value1 = 100.0R
            Dim value2 = 15.99R
            Dim result = client.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

' Call the Subtract service operation.
value1 = 145.00R
value2 = 76.54R
result = client.Subtract(value1, value2)
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

' Call the Multiply service operation.
value1 = 9.00R
value2 = 81.25R
result = client.Multiply(value1, value2)
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

' Call the Divide service operation.
value1 = 22.00R
value2 = 7.00R
result = client.Divide(value1, value2)
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

'Closing the client gracefully closes the connection and cleans up resources
```

```csharp
// Create a client.
CalculatorClient client = new CalculatorClient();

// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = client.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

// Call the Subtract service operation.
value1 = 145.00D;
value2 = 76.54D;
result = client.Subtract(value1, value2);
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

// Call the Multiply service operation.
value1 = 9.00D;
value2 = 81.25D;
result = client.Multiply(value1, value2);
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

// Call the Divide service operation.
value1 = 22.00D;
value2 = 7.00D;
result = client.Divide(value1, value2);
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

//Closing the client releases all communication resources.
client.Close();
```

<span data-ttu-id="22303-148">Wenn Sie das Beispiel ausführen, werden die Anforderungen und Antworten für den Vorgang im Clientkonsolenfenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="22303-148">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="22303-149">Drücken Sie im Clientfenster die EINGABETASTE, um den Client zu schließen.</span><span class="sxs-lookup"><span data-stu-id="22303-149">Press ENTER in the client window to shut down the client.</span></span>

```output
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

<span data-ttu-id="22303-150">Im Beispiel "Erste Schritte" wird der Standard zum Erstellen eines Diensts oder Clients veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="22303-150">The Getting Started sample shows the standard way to create a service and client.</span></span> <span data-ttu-id="22303-151">Der andere [grundlegende](basic-sample.md) Build in diesem Beispiel, um bestimmte Produkt Features zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="22303-151">The other [Basic](basic-sample.md) build on this sample to demonstrate specific product features.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="22303-152">So können Sie das Beispiel einrichten, erstellen und ausführen</span><span class="sxs-lookup"><span data-stu-id="22303-152">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="22303-153">Stellen Sie sicher, dass Sie das [einmalige Setup Verfahren für die Windows Communication Foundation Beispiele](one-time-setup-procedure-for-the-wcf-samples.md)ausgeführt haben.</span><span class="sxs-lookup"><span data-stu-id="22303-153">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="22303-154">Um die C#- oder Visual Basic .NET-Edition der Projektmappe zu erstellen, befolgen Sie die unter [Building the Windows Communication Foundation Samples](building-the-samples.md)aufgeführten Anweisungen.</span><span class="sxs-lookup"><span data-stu-id="22303-154">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="22303-155">Um das Beispiel in einer Konfiguration mit einem Computer oder Computer übergreifend auszuführen, befolgen Sie die Anweisungen unter [Ausführen der Windows Communication Foundation Beispiele](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="22303-155">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="22303-156">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="22303-156">See also</span></span>

- [<span data-ttu-id="22303-157">Vorgehensweise: Hosten eines WCF-Diensts in einer verwalteten Anwendung</span><span class="sxs-lookup"><span data-stu-id="22303-157">How to: Host a WCF Service in a Managed Application</span></span>](../how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="22303-158">Vorgehensweise: Hosten eines WCF-Diensts in IIS</span><span class="sxs-lookup"><span data-stu-id="22303-158">How to: Host a WCF Service in IIS</span></span>](../feature-details/how-to-host-a-wcf-service-in-iis.md)
