---
title: AJAX-Dienst mit HTTP POST
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: 143585b40a493983b7265971a17224165de6f36d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575887"
---
# <a name="ajax-service-using-http-post"></a><span data-ttu-id="51001-102">AJAX-Dienst mit HTTP POST</span><span class="sxs-lookup"><span data-stu-id="51001-102">AJAX Service Using HTTP POST</span></span>

<span data-ttu-id="51001-103">In diesem Beispiel wird veranschaulicht, wie Windows Communication Foundation (WCF) verwendet wird, um einen ASP.NET Asynchronous JavaScript and XML (Ajax)-Dienst zu erstellen, der HTTP Post verwendet.</span><span class="sxs-lookup"><span data-stu-id="51001-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that uses HTTP POST.</span></span> <span data-ttu-id="51001-104">Bei einem AJAX-Dienst handelt es sich um einen Dienst, auf den Sie mit einfachem JavaScript-Code von einem Webbrowserclient aus zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="51001-104">An AJAX service is one that you can access by using basic JavaScript code from a Web browser client.</span></span> <span data-ttu-id="51001-105">Dieses Beispiel baut auf dem Beispiel für den [grundlegenden AJAX-Dienst](basic-ajax-service.md) auf. der einzige Unterschied zwischen den beiden Beispielen besteht in der Verwendung von HTTP Post anstelle von HTTP Get.</span><span class="sxs-lookup"><span data-stu-id="51001-105">This sample builds on the [Basic AJAX Service](basic-ajax-service.md) sample; the only difference between the two samples is the use of HTTP POST instead of HTTP GET.</span></span>

<span data-ttu-id="51001-106">Die AJAX-Unterstützung in Windows Communication Foundation (WCF) ist für die Verwendung mit ASP.NET AJAX über das-Steuerelement optimiert `ScriptManager` .</span><span class="sxs-lookup"><span data-stu-id="51001-106">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="51001-107">Ein Beispiel für die Verwendung von WCF mit ASP.NET AJAX finden Sie in den [AJAX-Beispielen](ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="51001-107">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](ajax-service-using-http-post.md).</span></span>

> [!NOTE]
> <span data-ttu-id="51001-108">Die Setupprozedur und die Buildanweisungen für dieses Beispiel befinden sich am Ende dieses Themas.</span><span class="sxs-lookup"><span data-stu-id="51001-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="51001-109">Der Dienst im folgenden Beispiel ist ein WCF-Dienst ohne AJAX-spezifischen Code.</span><span class="sxs-lookup"><span data-stu-id="51001-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span>

<span data-ttu-id="51001-110">Wenn das- <xref:System.ServiceModel.Web.WebInvokeAttribute> Attribut auf einen Vorgang angewendet wird oder das- <xref:System.ServiceModel.Web.WebGetAttribute> Attribut nicht angewendet wird, wird das HTTP-Standard Verb ("Post") verwendet.</span><span class="sxs-lookup"><span data-stu-id="51001-110">If the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute is applied on an operation, or the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="51001-111">POST-Anforderungen sind schwieriger zu erstellen als GET-Anforderungen, sie werden jedoch nicht zwischengespeichert. Verwenden Sie POST-Anforderungen für alle Vorgänge, bei denen keine Zwischenspeicherung benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="51001-111">POST requests are harder to construct than GET requests, but they are not cached; use POST requests for all operations where caching is not appropriate.</span></span>

```csharp
[ServiceContract(Namespace = "PostAjaxService")]
public interface ICalculator
{
    [WebInvoke]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

<span data-ttu-id="51001-112">Erstellen Sie im Dienst mithilfe von <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> einen AJAX-Endpunkt wie im Beispiel "Einfacher AJAX-Dienst".</span><span class="sxs-lookup"><span data-stu-id="51001-112">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>

<span data-ttu-id="51001-113">Im Gegensatz zu GET-Anforderungen können Sie POST-Dienste nicht aus dem Browser aufrufen.</span><span class="sxs-lookup"><span data-stu-id="51001-113">Unlike GET requests, you cannot invoke POST services from the browser.</span></span> <span data-ttu-id="51001-114">Beispielsweise führt die Navigation zu zu `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` einem Fehler, da der Post-Dienst erwartet, dass der `n1` -Parameter und der- `n2` Parameter im Nachrichtentext im JSON-Format und nicht in der URL gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="51001-114">For example, navigating to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` results in an error, because the POST service expects the `n1` and `n2` parameters to be sent in the message body in the JSON format, and not in the URL.</span></span>

<span data-ttu-id="51001-115">Die Clientwebseite "PostAjaxClientPage.aspx" enthält ASP.NET-Code zum Aufrufen des Diensts, wenn der Benutzer auf eine der Vorgangsschaltflächen auf der Seite klickt.</span><span class="sxs-lookup"><span data-stu-id="51001-115">The client Web page PostAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="51001-116">Der Dienst antwortet auf die gleiche Weise wie im [grundlegenden AJAX-Dienst](basic-ajax-service.md) Beispiel mit der Get-Anforderung.</span><span class="sxs-lookup"><span data-stu-id="51001-116">The service responds in the same way as in the [Basic AJAX Service](basic-ajax-service.md) sample, with the GET request.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51001-117">Die Beispiele sind möglicherweise bereits auf dem Computer installiert.</span><span class="sxs-lookup"><span data-stu-id="51001-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="51001-118">Suchen Sie nach dem folgenden Verzeichnis (Standardverzeichnis), bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="51001-118">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="51001-119">Wenn dieses Verzeichnis nicht vorhanden ist, wechseln Sie zu [Windows Communication Foundation (WCF) und Windows Workflow Foundation (WF)-Beispiele für .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , um alle Windows Communication Foundation (WCF) und Beispiele herunterzuladen [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="51001-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="51001-120">Dieses Beispiel befindet sich im folgenden Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="51001-120">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="51001-121">So können Sie das Beispiel einrichten, erstellen und ausführen</span><span class="sxs-lookup"><span data-stu-id="51001-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="51001-122">Stellen Sie sicher, dass Sie die Setup Anweisungen [zum einmaligen Setup Verfahren für die Windows Communication Foundation Beispiele](one-time-setup-procedure-for-the-wcf-samples.md)ausführen.</span><span class="sxs-lookup"><span data-stu-id="51001-122">Ensure that you perform the setup instructions [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="51001-123">Erstellen Sie die Projekt Mappe "PostAjaxService. sln", wie unter [Erstellen der Windows Communication Foundation Beispiele](building-the-samples.md)beschrieben.</span><span class="sxs-lookup"><span data-stu-id="51001-123">Build the solution PostAjaxService.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="51001-124">Navigieren Sie zu `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (Öffnen Sie "PostAjaxClientPage. aspx" im Browser nicht aus dem Projektverzeichnis).</span><span class="sxs-lookup"><span data-stu-id="51001-124">Navigate to `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (do not open PostAjaxClientPage.aspx in the browser from the project directory).</span></span>
