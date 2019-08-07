---
title: Implementieren von API-Gateways mit Ocelot
description: Hier erfahren Sie, wie Sie API-Gateways mit Ocelot implementieren und Ocelot in einer containerbasierten Umgebung verwenden.
ms.date: 10/02/2018
ms.openlocfilehash: 2a1c7b0f4baa979864ac32d555f65397531884b8
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676187"
---
# <a name="implement-api-gateways-with-ocelot"></a><span data-ttu-id="22245-103">Implementieren von API-Gateways mit Ocelot</span><span class="sxs-lookup"><span data-stu-id="22245-103">Implement API Gateways with Ocelot</span></span>

<span data-ttu-id="22245-104">Die Microservice-Referenzanwendung [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) verwendet [Ocelot](https://github.com/ThreeMammals/Ocelot), ein einfaches und leichtes API-Gateway, das Sie überall zusammen mit Ihren Microservices/Containern beispielsweise in einer der folgenden von eShopOnContainers verwendeten Umgebungen bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="22245-104">The reference microservice application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) is using [Ocelot](https://github.com/ThreeMammals/Ocelot), a simple and lightweight API Gateway that you can deploy anywhere along with your microservices/containers, such as in any of the following environments used by eShopOnContainers.</span></span>

- <span data-ttu-id="22245-105">Docker-Host: auf Ihrem lokalen Entwicklungs-PC, lokal oder in der Cloud</span><span class="sxs-lookup"><span data-stu-id="22245-105">Docker host, in your local dev PC, on-premises or in the cloud.</span></span>
- <span data-ttu-id="22245-106">Kubernetes-Cluster: lokal oder in einer verwalteten Cloud wie Azure Kubernetes Service (AKS)</span><span class="sxs-lookup"><span data-stu-id="22245-106">Kubernetes cluster, on-premises or in managed cloud such as Azure Kubernetes Service (AKS).</span></span>
- <span data-ttu-id="22245-107">Service Fabric-Cluster: lokal oder in der Cloud</span><span class="sxs-lookup"><span data-stu-id="22245-107">Service Fabric cluster, on-premises or in the cloud.</span></span>
- <span data-ttu-id="22245-108">Service Fabric-Mesh: als PaaS/Serverless in Azure</span><span class="sxs-lookup"><span data-stu-id="22245-108">Service Fabric mesh, as PaaS/Serverless in Azure.</span></span>

## <a name="architect-and-design-your-api-gateways"></a><span data-ttu-id="22245-109">Erstellen und Entwerfen der API-Gateways</span><span class="sxs-lookup"><span data-stu-id="22245-109">Architect and design your API Gateways</span></span>

<span data-ttu-id="22245-110">In der folgenden Abbildung ist die Implementierung von API-Gateways mit Ocelot in eShopOnContainers dargestellt.</span><span class="sxs-lookup"><span data-stu-id="22245-110">The following architecture diagram shows how API Gateways are implemented with Ocelot in eShopOnContainers.</span></span>

![Darstellung der eShopOnContainers-Architektur mit Client-Apps, Microservices und den dazwischengeschalteten API-Gateways](./media/image28.png)

<span data-ttu-id="22245-112">**Abbildung 6-28**.</span><span class="sxs-lookup"><span data-stu-id="22245-112">**Figure 6-28**.</span></span> <span data-ttu-id="22245-113">eShopOnContainers-Architektur mit API-Gateways</span><span class="sxs-lookup"><span data-stu-id="22245-113">eShopOnContainers architecture with API Gateways</span></span>

<span data-ttu-id="22245-114">In dieser Abbildung wird dargestellt, wie die gesamte Anwendung in einem Docker-Host oder Entwicklungs-PC mit Docker für Windows oder Docker für Mac bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="22245-114">That diagram shows how the whole application is deployed into a single Docker host or development PC with “Docker for Windows” or “Docker for Mac”.</span></span> <span data-ttu-id="22245-115">Die Bereitstellung in einem Orchestrator erfolgt im Wesentlichen auf dieselbe Weise, jedoch können alle Container in der Abbildung im Orchestrator horizontal skaliert werden.</span><span class="sxs-lookup"><span data-stu-id="22245-115">However, deploying into any orchestrator would be pretty similar but any container in the diagram could be scaled-out in the orchestrator.</span></span>

<span data-ttu-id="22245-116">Ferner müssen die Infrastrukturressourcen wie Datenbanken, Cache und Nachrichtenbroker vom Orchestrator ausgelagert und in hochverfügbaren Systemen für Infrastruktur wie Azure SQL-Datenbank, Azure Cosmos DB, Azure Redis, Azure Service Bus oder in einer lokalen Clusterlösung mit Hochverfügbarkeit bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="22245-116">In addition, the infrastructure assets such as databases, cache, and message brokers should be offloaded from the orchestrator and deployed into high available systems for infrastructure, like Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus, or any HA clustering solution on-premises.</span></span>

<span data-ttu-id="22245-117">Wie der Abbildung außerdem zu entnehmen ist, können bei Verwendung mehrerer API-Gateways mehrere Entwicklungsteams autonom (in diesem Beispiel Marketingfeatures und Einkaufsfeatures) bei der Entwicklung und Bereitstellung ihrer Microservices und ihrer eigenen zugehörigen API-Gateways arbeiten.</span><span class="sxs-lookup"><span data-stu-id="22245-117">As you can also notice in the diagram, having several API Gateways allows multiple development teams to be autonomous (in this case Marketing features vs. Shopping features) when developing and deploying their microservices plus their own related API Gateways.</span></span>

<span data-ttu-id="22245-118">Bei nur einem monolithischen API-Gateway müsste eine zentrale Stelle von verschiedenen Entwicklungsteams aktualisiert werden, wodurch alle Microservices mit einem Teil der Anwendung gekoppelt werden könnten.</span><span class="sxs-lookup"><span data-stu-id="22245-118">If you had a single monolithic API Gateway that would mean a single point to be updated by several development teams, which could couple all the microservices with a single part of the application.</span></span>

<span data-ttu-id="22245-119">Wesentlich weiter im Design kann ein differenziertes API-Gateway je nach gewählter Architektur mitunter auf einen einzelnen Unternehmensmicroservice beschränkt sein.</span><span class="sxs-lookup"><span data-stu-id="22245-119">Going much further in the design, sometimes a fine-grained API Gateway can also be limited to a single business microservice depending on the chosen architecture.</span></span> <span data-ttu-id="22245-120">Wenn die Einschränkungen des API-Gateways vom Unternehmen oder von der Domäne vorgegeben sind, können Sie auf einfache Weise ein besseres Design erstellen.</span><span class="sxs-lookup"><span data-stu-id="22245-120">Having the API Gateway’s boundaries dictated by the business or domain will help you to get a better design.</span></span>

<span data-ttu-id="22245-121">Auf der Ebene des API-Gateways kann Granularität beispielsweise für erweiterte zusammengesetzte Benutzeroberflächenanwendungen, die auf Microservices basieren, besonders nützlich sein, da das Konzept eines präzisen API-Gateways einem Dienst zur Benutzeroberflächenkomposition ähnelt.</span><span class="sxs-lookup"><span data-stu-id="22245-121">For instance, fine granularity in the API Gateway tier can be especially useful for more advanced composite UI applications that are based on microservices, because the concept of a fine-grained API Gateway is similar to a UI composition service.</span></span>

<span data-ttu-id="22245-122">Im vorherigen Abschnitt [Creating composite UI based on microservices (Erstellen einer zusammengesetzten Benutzeroberfläche auf der Grundlage von Microservices)](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md) haben wir uns damit eingehend befasst.</span><span class="sxs-lookup"><span data-stu-id="22245-122">We delve into more details in the previous section [Creating composite UI based on microservices](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).</span></span>

<span data-ttu-id="22245-123">Wichtig ist, dass sich bei vielen mittelgroßen und großen Anwendungen die Verwendung eines kundenspezifischen API-Gatewayprodukts anbietet. Dieses API-Gateway sollte jedoch nur dann als einzelner monolithischer Aggregator oder als exklusives benutzerdefiniertes zentrales API-Gateway eingesetzt werden, wenn es für die verschiedenen Entwicklungsteams, die autonome Microservices erstellen, mehrere unabhängige Konfigurationsbereiche zulässt.</span><span class="sxs-lookup"><span data-stu-id="22245-123">As key takeaway, for many medium- and large-size applications, using a custom-built API Gateway product is usually a good approach, but not as a single monolithic aggregator or unique central custom API Gateway unless that API Gateway allows multiple independent configuration areas for the several development teams creating autonomous microservices.</span></span>

### <a name="sample-microservicescontainers-to-re-route-through-the-api-gateways"></a><span data-ttu-id="22245-124">Beispiele für Microservices bzw. Container, die über die API-Gateways umgeleitet werden</span><span class="sxs-lookup"><span data-stu-id="22245-124">Sample microservices/containers to re-route through the API Gateways</span></span>

<span data-ttu-id="22245-125">eShopOnContainers enthält beispielsweise etwa sechs interne Microservicetypen, die, wie in der Abbildung dargestellt, über die API-Gateways veröffentlicht werden sollen.</span><span class="sxs-lookup"><span data-stu-id="22245-125">As an example, eShopOnContainers has around six internal microservice-types that have to be published through the API Gateways, as shown in the following image.</span></span>

![Nur die Microservices „Basket“ (Warenkorb), „Catalog“ (Katalog), „Location“ (Speicherort), „Marketing“ (Marketing), „Ordering“ (Reihenfolge) und „Payment“ (Bezahlung) werden über das API-Gateway veröffentlicht.](./media/image29.png)

<span data-ttu-id="22245-127">**Abbildung 6-29**.</span><span class="sxs-lookup"><span data-stu-id="22245-127">**Figure 6-29**.</span></span> <span data-ttu-id="22245-128">Microserviceordner in eShopOnContainers-Projektmappe in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="22245-128">Microservice folders in eShopOnContainers solution in Visual Studio</span></span>

<span data-ttu-id="22245-129">Der Microservice „Identity“ wurde im Design aus dem API-Gatewayrouting ausgelassen, da es sich hierbei um den einzigen übergreifenden Belang im System handelt. Mit Ocelot kann er jedoch auch als Teil der Umleitungslisten einbezogen werden.</span><span class="sxs-lookup"><span data-stu-id="22245-129">About the Identity service, in the design it's left out of the API Gateway routing because it's the only cross-cutting concern in the system, although with Ocelot it's also possible to include it as part of the rerouting lists.</span></span>

<span data-ttu-id="22245-130">Wie anhand des Codes zu erkennen ist, sind diese Microservices derzeit alle als ASP.NET Core Web-API-Microservices implementiert.</span><span class="sxs-lookup"><span data-stu-id="22245-130">All those services are currently implemented as ASP.NET Core Web API services, as you can tell from the code.</span></span> <span data-ttu-id="22245-131">Betrachten wir nun einen der Microservices etwas genauer, wie etwa den Code des Microservices „Catalog“.</span><span class="sxs-lookup"><span data-stu-id="22245-131">Let’s focus on one of the microservices like the Catalog microservice code.</span></span>

![Projektmappen-Explorer-Ansicht des Catalog.API-Projekts.](./media/image30.png)

<span data-ttu-id="22245-133">**Abbildung 6-30**.</span><span class="sxs-lookup"><span data-stu-id="22245-133">**Figure 6-30**.</span></span> <span data-ttu-id="22245-134">Beispiel für einen Web-API-Microservice (Microservice „Catalog“)</span><span class="sxs-lookup"><span data-stu-id="22245-134">Sample Web API microservice (Catalog microservice)</span></span>

<span data-ttu-id="22245-135">Es ist zu erkennen, dass der Microservice „Catalog“ ein typisches ASP.NET Core Web-API-Projekt mit mehreren Controllern und Methoden wie im folgenden Code ist.</span><span class="sxs-lookup"><span data-stu-id="22245-135">You can see that the Catalog microservice is a typical ASP.NET Core Web API project with several controllers and methods like in the following code.</span></span>

```csharp
[HttpGet]
[Route("items/{id:int}")]
[ProducesResponseType((int)HttpStatusCode.BadRequest)]
[ProducesResponseType((int)HttpStatusCode.NotFound)]
[ProducesResponseType(typeof(CatalogItem),(int)HttpStatusCode.OK)]
public async Task<IActionResult> GetItemById(int id)
{
    if (id <= 0)
    {
        return BadRequest();
    }
    var item = await _catalogContext.CatalogItems.
                                          SingleOrDefaultAsync(ci => ci.Id == id);
    //…

    if (item != null)
    {
        return Ok(item);
    }
    return NotFound();
}
```

<span data-ttu-id="22245-136">Die HTTP-Anforderung führt letztendlich diese Art von C#-Code durch Zugriff auf die Microservicedatenbank sowie alle weiteren erforderlichen Aktionen aus.</span><span class="sxs-lookup"><span data-stu-id="22245-136">The HTTP request will end up running that kind of C# code accessing the microservice database and any additional required action.</span></span>

<span data-ttu-id="22245-137">Mit Blick auf die Microservice-URL wird bei der Bereitstellung der Container im lokalen Entwicklungs-PC (lokalen Docker-Host) wie in der folgenden Dockerfile-Datei angegeben für jeden Container eines Microservices in der entsprechenden Dockerfile-Datei ein interner Port (meist Port 80):</span><span class="sxs-lookup"><span data-stu-id="22245-137">Regarding the microservice URL, when the containers are deployed in your local development PC (local Docker host), each microservice’s container has always an internal port (usually port 80) specified in its dockerfile, as in the following dockerfile:</span></span>

```Dockerfile
FROM microsoft/aspnetcore:2.0.5 AS base
WORKDIR /app
EXPOSE 80
```

<span data-ttu-id="22245-138">Der im Code angegebene Port 80 ist ein interner Port im Docker-Host, auf den Client-Apps nicht zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="22245-138">The port 80 shown in the code is internal within the Docker host, so it can't be reached by client apps.</span></span>

<span data-ttu-id="22245-139">Client-Apps können nur auf die externen Ports zugreifen (sofern vorhanden), die bei der Bereitstellung mit `docker-compose` veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="22245-139">Client apps can access only the external ports (if any) published when deploying with `docker-compose`.</span></span>

<span data-ttu-id="22245-140">Diese externen Ports dürfen bei der Bereitstellung in einer Produktionsumgebung nicht veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="22245-140">Those external ports shouldn't be published when deploying to a production environment.</span></span> <span data-ttu-id="22245-141">Aus diesem Grund sollten Sie das API-Gateway verwenden, um die direkte Kommunikation zwischen den Client-Apps und den Microservices zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="22245-141">This is precisely why you want to use the API Gateway, to avoid the direct communication between the client apps and the microservices.</span></span>

<span data-ttu-id="22245-142">Beim Entwickeln möchten Sie jedoch auf den Microservice bzw. auf den Container direkt zugreifen und den Microservice bzw. den Container über Swagger ausführen.</span><span class="sxs-lookup"><span data-stu-id="22245-142">However, when developing, you want to access the microservice/container directly and run it through Swagger.</span></span> <span data-ttu-id="22245-143">Daher werden die externen Ports in eShopOnContainers dennoch angegeben, auch wenn sie vom API-Gateway oder den Client-Apps nicht verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="22245-143">That’s why in eShopOnContainers, the external ports are still specified even when they won’t be used by the API Gateway or the client apps.</span></span>

<span data-ttu-id="22245-144">Das folgende Beispiel zeigt die Datei `docker-compose.override.yml` für den Microservice „Catalog“:</span><span class="sxs-lookup"><span data-stu-id="22245-144">Here’s an example of the `docker-compose.override.yml` file for the Catalog microservice:</span></span>

```yml
catalog.api:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:80
    - ConnectionString=YOUR_VALUE
    - ... Other Environment Variables
  ports:
    - "5101:80"   # Important: In a production environment you should remove the external port (5101) kept here for microservice debugging purposes.
                  # The API Gateway redirects and access through the internal port (80).
```

<span data-ttu-id="22245-145">Wie Sie sehen, wurde in der Datei „docker-compose.override.yml“ Port 80 als interner Port für den Container „Catalog“ konfiguriert, für den externen Zugriff jedoch Port 5101.</span><span class="sxs-lookup"><span data-stu-id="22245-145">You can see how in the docker-compose.override.yml configuration the internal port for the Catalog container is port 80, but the port for external access is 5101.</span></span> <span data-ttu-id="22245-146">Dieser Port sollte bei Verwendung eines API-Gateways von der Anwendung jedoch nur zum Debuggen, Ausführen und Testen des Microservice „Catalog“ verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="22245-146">But this port shouldn’t be used by the application when using an API Gateway, only to debug, run and test just the Catalog microservice.</span></span>

<span data-ttu-id="22245-147">Normalerweise würde die Bereitstellung mit „docker-compose“ nicht in einer Produktionsumgebung stattfinden, da die richtige Produktionsbereitstellungsumgebung für Microservices ein Orchestrator wie Kubernetes oder Service Fabric ist.</span><span class="sxs-lookup"><span data-stu-id="22245-147">Normally, you won’t be deploying with docker-compose into a production environment because the right production deployment environment for microservices is an orchestrator like Kubernetes or Service Fabric.</span></span> <span data-ttu-id="22245-148">Bei einer Bereitstellung in diesen Umgebungen verwenden Sie unterschiedliche Konfigurationsdateien, wenn Sie nicht direkt einen externen Port für Microservices veröffentlichen möchten. Sie verwenden jedoch immer den Reverseproxy aus dem API-Gateway.</span><span class="sxs-lookup"><span data-stu-id="22245-148">When deploying to those environments you use different configuration files where you won’t publish directly any external port for the microservices but, you'll always use the reverse proxy from the API Gateway.</span></span>

<span data-ttu-id="22245-149">Führen Sie den Microservice „Catalog“ in Ihrem lokalen Docker-Host aus, indem Sie entweder die gesamte eShopOnContainers-Projektmappe aus Visual Studio (dabei werden alle Microservices in den „docker-compose“-Dateien ausgeführt) ausführen oder nur den Microservice „Catalog“ mit dem folgenden „docker-compose“-Befehl in CMD oder PowerShell in dem Ordner starten, in dem sich die Dateien `docker-compose.yml` und „docker-compose.override.yml“ befinden.</span><span class="sxs-lookup"><span data-stu-id="22245-149">Run the catalog microservice in your local Docker host either by running the full eShopOnContainers solution from Visual Studio (it’ll run all the services in the docker-compose files) or just starting the Catalog microservice with the following docker-compose command in CMD or PowerShell positioned at the folder where the `docker-compose.yml` and docker-compose.override.yml are placed.</span></span>

```console
docker-compose run --service-ports catalog.api
```

<span data-ttu-id="22245-150">Mit diesem Befehl werden nur der Dienstcontainer „catalog.api“ sowie die Abhängigkeiten ausgeführt, die in der Datei „docker-compose.yml“ angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="22245-150">This command only runs the catalog.api service container plus dependencies that are specified in the docker-compose.yml.</span></span> <span data-ttu-id="22245-151">In diesem Beispiel sind das die Container „SQL Server“ und „RabbitMQ“.</span><span class="sxs-lookup"><span data-stu-id="22245-151">In this case, the SQL Server container and RabbitMQ container.</span></span>

<span data-ttu-id="22245-152">Anschließend können Sie direkt auf den Microservice „Catalog“ zugreifen und die zugehörigen Methoden über die Swagger-Benutzeroberfläche direkt über diesen „externen“ Port (in diesem Beispiel `http://localhost:5101/swagger`) anzeigen:</span><span class="sxs-lookup"><span data-stu-id="22245-152">Then, you can directly access the Catalog microservice and see its methods through the Swagger UI accessing directly through that “external” port, in this case `http://localhost:5101/swagger`:</span></span>

![Browseransicht der Swagger-Benutzeroberfläche mit der Seite für die Catalog.API REST-API.](./media/image31.png)

<span data-ttu-id="22245-154">**Abbildung 6-31**.</span><span class="sxs-lookup"><span data-stu-id="22245-154">**Figure 6-31**.</span></span> <span data-ttu-id="22245-155">Testen des Microservice „Catalog“ mit der Swagger-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="22245-155">Testing the Catalog microservice with its Swagger UI</span></span>

<span data-ttu-id="22245-156">An dieser Stelle könnten Sie einen Haltepunkt im C#-Code in Visual Studio festlegen, den Microservice mit den in der Swagger-Benutzeroberfläche angezeigten Methoden testen und schließlich mit dem Befehl `docker-compose down` alles bereinigen.</span><span class="sxs-lookup"><span data-stu-id="22245-156">At this point, you could set a breakpoint in C# code in Visual Studio, test the microservice with the methods exposed in Swagger UI, and finally clean-up everything with the `docker-compose down` command.</span></span>

<span data-ttu-id="22245-157">Direkte Kommunikation mit dem Microservice, in diesem Beispiel über den externen Port 5101, sollten Sie in Ihrer Anwendung jedoch vermeiden.</span><span class="sxs-lookup"><span data-stu-id="22245-157">However, direct-access communication to the microservice, in this case through the external port 5101, is precisely what you want to avoid in your application.</span></span> <span data-ttu-id="22245-158">Sie können sie vermeiden, indem Sie die zusätzliche Dereferenzierungsebene des API-Gateways (in diesem Beispiel Ocelot) festlegen.</span><span class="sxs-lookup"><span data-stu-id="22245-158">And you can avoid that by setting the additional level of indirection of the API Gateway (Ocelot, in this case).</span></span> <span data-ttu-id="22245-159">Auf diese Weise greift die Client-App nicht direkt auf den Microservice zu.</span><span class="sxs-lookup"><span data-stu-id="22245-159">That way, the client app won’t directly access the microservice.</span></span>

## <a name="implementing-your-api-gateways-with-ocelot"></a><span data-ttu-id="22245-160">Implementieren von API-Gateways mit Ocelot</span><span class="sxs-lookup"><span data-stu-id="22245-160">Implementing your API Gateways with Ocelot</span></span>

<span data-ttu-id="22245-161">Bei Ocelot handelt es sich im Grunde um mehrere Middlewares, die Sie in einer bestimmten Reihenfolge anwenden können.</span><span class="sxs-lookup"><span data-stu-id="22245-161">Ocelot is basically a set of middlewares that you can apply in a specific order.</span></span>

<span data-ttu-id="22245-162">Ocelot wurde speziell nur für ASP.NET Core entwickelt.</span><span class="sxs-lookup"><span data-stu-id="22245-162">Ocelot is designed to work with ASP.NET Core only.</span></span> <span data-ttu-id="22245-163">Ocelot bezieht sich auf .NET Standard 2.0 und kann somit immer dann verwendet werden, wenn .NET Standard 2.0 unterstützt wird, wie etwa für .NET Core Runtime 2.0 und .NET Framework-Runtime ab Version 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="22245-163">It targets netstandard2.0 so it can be used anywhere .NET Standard 2.0 is supported, including .NET Core 2.0 runtime and .NET Framework 4.6.1 runtime and up.</span></span>

<span data-ttu-id="22245-164">Installieren Sie Ocelot und die zugehörigen Abhängigkeiten in Ihrem ASP.NET Core-Projekt mit dem [NuGet-Paket für Ocelot](https://www.nuget.org/packages/Ocelot/) über Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="22245-164">You install Ocelot and its dependencies in your ASP.NET Core project with [Ocelot's NuGet package](https://www.nuget.org/packages/Ocelot/), from Visual Studio.</span></span>

```powershell
Install-Package Ocelot
```

<span data-ttu-id="22245-165">In eShopOnContainers ist die API-Gateway-Implementierung ein einfaches ASP.NET Core WebHost-Projekt. Für die API-Gatewayfeatures ist wie in der folgenden Abbildung dargestellt die Middleware von Ocelot zuständig:</span><span class="sxs-lookup"><span data-stu-id="22245-165">In eShopOnContainers, its API Gateway implementation is a simple ASP.NET Core WebHost project, and Ocelot’s middlewares handle all the API Gateway features, as shown in the following image:</span></span>

![Projektmappen-Explorer-Ansicht des API-Gateway-Projekts für Ocelot.](./media/image32.png)

<span data-ttu-id="22245-167">**Abbildung 6-32**.</span><span class="sxs-lookup"><span data-stu-id="22245-167">**Figure 6-32**.</span></span> <span data-ttu-id="22245-168">Das Basisprojekt „OcelotApiGw“ in eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="22245-168">The OcelotApiGw base project in eShopOnContainers</span></span>

<span data-ttu-id="22245-169">Dieses ASP.NET Core-WebHost-Projekt besteht im Grunde aus zwei einfachen Dateien: `Program.cs` und `Startup.cs`.</span><span class="sxs-lookup"><span data-stu-id="22245-169">This ASP.NET Core WebHost project is basically built with two simple files:  `Program.cs` and `Startup.cs`.</span></span>

<span data-ttu-id="22245-170">Mit der Datei „Program.cs“ wird lediglich die typische ASP.NET Core-Methode „BuildWebHost“ erstellt und konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="22245-170">The Program.cs just needs to create and configure the typical ASP.NET Core BuildWebHost.</span></span>

```csharp
namespace OcelotApiGw
{
    public class Program
    {
        public static void Main(string[] args)
        {
            BuildWebHost(args).Run();
        }

        public static IWebHost BuildWebHost(string[] args)
        {
            var builder = WebHost.CreateDefaultBuilder(args);

            builder.ConfigureServices(s => s.AddSingleton(builder))
                    .ConfigureAppConfiguration(
                          ic => ic.AddJsonFile(Path.Combine("configuration",
                                                            "configuration.json")))
                    .UseStartup<Startup>();
            var host = builder.Build();
            return host;
        }
    }
}
```

<span data-ttu-id="22245-171">Wichtig für Ocelot ist die Datei `configuration.json`, die Sie dem Generator über die Methode `AddJsonFile()` bereitstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="22245-171">The important point here for Ocelot is the `configuration.json` file that you must provide to the builder through the `AddJsonFile()` method.</span></span> <span data-ttu-id="22245-172">In dieser `configuration.json`-Datei werden alle API-Gateway-Umleitungen, d.h. die externen Endpunkte mit bestimmten Ports und die entsprechenden internen Endpunkte (meist mit anderen Ports), angegeben.</span><span class="sxs-lookup"><span data-stu-id="22245-172">That `configuration.json` is where you specify all the API Gateway ReRoutes, meaning the external endpoints with specific ports and the correlated internal endpoints, usually using different ports.</span></span>

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

<span data-ttu-id="22245-173">Für die Konfiguration gibt es zwei Abschnitte:</span><span class="sxs-lookup"><span data-stu-id="22245-173">There are two sections to the configuration.</span></span> <span data-ttu-id="22245-174">„ReRoutes“ und „GlobalConfiguration“.</span><span class="sxs-lookup"><span data-stu-id="22245-174">An array of Re-Routes and a GlobalConfiguration.</span></span> <span data-ttu-id="22245-175">Bei „ReRoutes“ handelt es sich um die Objekte, die Ocelot mitteilen, wie eine Upstreamanforderung behandelt werden soll.</span><span class="sxs-lookup"><span data-stu-id="22245-175">The Re-Routes are the objects that tell Ocelot how to treat an upstream request.</span></span> <span data-ttu-id="22245-176">Mit „GlobalConfiguration“ können „ReRoute“-spezifische Einstellungen außer Kraft gesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="22245-176">The Global configuration allows overrides of Re-Route specific settings.</span></span> <span data-ttu-id="22245-177">Das ist hilfreich, wenn Sie vermeiden möchten, dass Sie zahlreiche „ReRoute“-spezifische Einstellungen verwalten müssen.</span><span class="sxs-lookup"><span data-stu-id="22245-177">It’s useful if you don’t want to manage lots of Re-Route specific settings.</span></span>

<span data-ttu-id="22245-178">Das folgende Beispiel zeigt eine vereinfachte [ReRoute-Konfigurationsdatei](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) aus einem der API-Gateways aus eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="22245-178">Here’s a simplified example of [ReRoute configuration file](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) from one of the API Gateways from eShopOnContainers.</span></span>

```json
{
  "ReRoutes": [
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "catalog.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/c/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ]
    },
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }

  ],
    "GlobalConfiguration": {
      "RequestIdKey": "OcRequestId",
      "AdministrationPath": "/administration"
    }
  }
```

<span data-ttu-id="22245-179">Ein Ocelot-API-Gateway hat in erster Linie die Aufgabe, eingehende HTTP-Anforderungen derzeit als eine andere HTTP-Anforderung an einen Downstreamdienst weiterzuleiten.</span><span class="sxs-lookup"><span data-stu-id="22245-179">The main functionality of an Ocelot API Gateway is to take incoming HTTP requests and forward them on to a downstream service, currently as another HTTP request.</span></span> <span data-ttu-id="22245-180">Bei Ocelot wird die Weiterleitung einer Anforderung an eine andere Anforderung als ReRoute beschrieben.</span><span class="sxs-lookup"><span data-stu-id="22245-180">Ocelot’s describes the routing of one request to another as a Re-Route.</span></span>

<span data-ttu-id="22245-181">Betrachten Sie beispielsweise eines der ReRoute-Objekte in der Datei „configuration.json“ weiter oben, die Konfiguration des Microservice „Basket“.</span><span class="sxs-lookup"><span data-stu-id="22245-181">For instance, let’s focus on one of the Re-Routes in the configuration.json from above, the configuration for the Basket microservice.</span></span>

```json
{
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
}
```

<span data-ttu-id="22245-182">„DownstreamPathTemplate“, „Scheme“ und „DownstreamHostAndPorts“ ergeben die interne Microservice-URL, an die diese Anforderung weitergeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="22245-182">The DownstreamPathTemplate, Scheme, and DownstreamHostAndPorts make the internal microservice URL that this request will be forwarded to.</span></span>

<span data-ttu-id="22245-183">Als Port wird der vom Microservice verwendete interne Port verwendet.</span><span class="sxs-lookup"><span data-stu-id="22245-183">The port is the internal port used by the service.</span></span> <span data-ttu-id="22245-184">Bei Verwendung von Containern wird der Port in der entsprechenden Dockerfile angegeben.</span><span class="sxs-lookup"><span data-stu-id="22245-184">When using containers, the port specified at its dockerfile.</span></span>

<span data-ttu-id="22245-185">`Host` ist ein Dienstname, der von der verwendeten Dienstnamensauflösung abhängt.</span><span class="sxs-lookup"><span data-stu-id="22245-185">The `Host` is a service name that depends on the service name resolution you are using.</span></span> <span data-ttu-id="22245-186">Bei Verwendung von „docker-compose“ werden die Dienstnamen vom Docker-Host bereitgestellt, der die in den „docker-compose“-Dateien bereitgestellten Dienstnamen verwendet.</span><span class="sxs-lookup"><span data-stu-id="22245-186">When using docker-compose, the services names are provided by the Docker Host, which is using the service names provided in the docker-compose files.</span></span> <span data-ttu-id="22245-187">Bei Verwendung eines Orchestrators wie Kubernetes oder Service Fabric sollte dieser Name durch die vom jeweiligen Orchestrator bereitgestellte DNS- oder Namensauflösung aufgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="22245-187">If using an orchestrator like Kubernetes or Service Fabric, that name should be resolved by the DNS or name resolution provided by each orchestrator.</span></span>

<span data-ttu-id="22245-188">Bei „DownstreamHostAndPorts“ handelt es sich um ein Array, das den Host und Port aller Downstreamdienste enthält, an die Sie Anforderungen weiterleiten möchten.</span><span class="sxs-lookup"><span data-stu-id="22245-188">DownstreamHostAndPorts is an array that contains the host and port of any downstream services that you wish to forward requests to.</span></span> <span data-ttu-id="22245-189">In der Regel ist nur ein Eintrag enthalten. Es kann jedoch vorkommen, dass Sie für Anforderungen einen Lastausgleich in Ihren Downstreamdiensten vornehmen möchten. Mit Ocelot können Sie mehrere Einträge hinzufügen und einen Lastausgleich auswählen.</span><span class="sxs-lookup"><span data-stu-id="22245-189">Usually this will just contain one entry but sometimes you might want to load balance requests to your downstream services and Ocelot lets you add more than one entry and then select a load balancer.</span></span> <span data-ttu-id="22245-190">Wenn Sie jedoch Azure und einen Orchestrator verwenden, sollten Sie einen Lastausgleich mit der Cloud- oder Orchestratorinfrastruktur vornehmen.</span><span class="sxs-lookup"><span data-stu-id="22245-190">But if using Azure and any orchestrator it is probably a better idea to load balance with the cloud and orchestrator infrastructure.</span></span>

<span data-ttu-id="22245-191">„UpstreamPathTemplate“ ist die URL, die von Ocelot verwendet wird, um zu bestimmen, welches DownstreamPathTemplate-Objekt für eine bestimmte Anforderung vom Client verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="22245-191">The UpstreamPathTemplate is the URL that Ocelot will use to identify which DownstreamPathTemplate to use for a given request from the client.</span></span> <span data-ttu-id="22245-192">„UpstreamHttpMethod“ wird verwendet, damit Ocelot zwischen unterschiedlichen Anforderungen (GET, POST, PUT) an dieselbe URL unterscheiden kann.</span><span class="sxs-lookup"><span data-stu-id="22245-192">Finally, the UpstreamHttpMethod is used so Ocelot can distinguish between different requests (GET, POST, PUT) to the same URL.</span></span>

<span data-ttu-id="22245-193">An dieser Stelle können Sie ein Ocelot-API-Gateway (ASP.NET Core WebHost) zusammen mit einem oder [mehreren zusammengeführten configuration.json-Dateien](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) verwenden oder die [Konfiguration in einem Consul-Schlüsselwertspeicher](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul) speichern.</span><span class="sxs-lookup"><span data-stu-id="22245-193">At this point, you could have a single Ocelot API Gateway (ASP.NET Core WebHost) using one or [multiple merged configuration.json files](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) or you can also store the [configuration in a Consul KV store](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span></span>

<span data-ttu-id="22245-194">Wie in den Abschnitten über Architektur und Design bereits erwähnt, sollten Sie bei Verwendung von autonomen Microservices dieses monolithische API-Gateway jedoch in mehrere API-Gateways und/oder BFFs (Backend for Frontend) aufteilen.</span><span class="sxs-lookup"><span data-stu-id="22245-194">But as introduced in the architecture and design sections, if you really want to have autonomous microservices, it might be better to split that single monolithic API Gateway into multiple API Gateways and/or BFF (Backend for Frontend).</span></span> <span data-ttu-id="22245-195">Betrachten wir dazu, wie dieser Ansatz mit Docker-Containern implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="22245-195">For that purpose, let’s see how to implement that approach with Docker containers.</span></span>

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a><span data-ttu-id="22245-196">Verwenden eines Docker-Containerimages zum Ausführen von verschiedenen API-Gateway-/BFF-Containertypen</span><span class="sxs-lookup"><span data-stu-id="22245-196">Using a single Docker container image to run multiple different API Gateway / BFF container types</span></span>

<span data-ttu-id="22245-197">In eShopOnContainers verwenden wir ein Docker-Containerimage mit dem Ocelot-API-Gateway. Bei Laufzeit erstellen wir für die einzelnen API-Gatewaytypen/BFF-Typen jedoch andere Microservices bzw. Container, indem eine andere configuration.json-Datei bereitgestellt wird. Dazu wird ein Docker-Volume verwendet, um für jeden Dienst auf einen anderen PC-Ordner zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="22245-197">In eShopOnContainers we’re using a single Docker container image with the Ocelot API Gateway but then, at run time, we create different services/containers for each type of API-Gateway/BFF by providing a different configuration.json file, using a docker volume to access a different PC folder for each service.</span></span>

![Ein einziges Docker-Image für das Ocelot-API-Gateway wird für alle vier API-Gateways verwendet.](./media/image33.png)

<span data-ttu-id="22245-199">**Abbildung 6-33**.</span><span class="sxs-lookup"><span data-stu-id="22245-199">**Figure 6-33**.</span></span> <span data-ttu-id="22245-200">Wiederverwenden eines Ocelot-Docker-Images für mehrere API-Gatewaytypen</span><span class="sxs-lookup"><span data-stu-id="22245-200">Re-using a single Ocelot Docker image across multiple API Gateway types</span></span>

<span data-ttu-id="22245-201">In eShopOnContainers wird das „generische Ocelot-API-Gateway-Docker-Image“ mit dem Projekt „OcelotApiGw“ und dem Imagenamen „eshop/ocelotapigw“ erstellt, das in der Datei „docker-compose.yml“ angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="22245-201">In eShopOnContainers, the “Generic Ocelot API Gateway Docker Image” is created with the project named 'OcelotApiGw' and the image name “eshop/ocelotapigw” that is specified in the docker-compose.yml file.</span></span> <span data-ttu-id="22245-202">Bei der Bereitstellung in Docker werden aus diesem Docker-Image wie im folgenden Auszug aus der Datei „docker-compose.yml“ vier API-Gateway-Container erstellt.</span><span class="sxs-lookup"><span data-stu-id="22245-202">Then, when deploying to Docker, there will be four API-Gateway containers created from that same Docker image, as shown in the following extract from the docker-compose.yml file.</span></span>

```yml
  mobileshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  mobilemarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webmarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile
```

<span data-ttu-id="22245-203">Wie Sie im folgenden Auszug aus der Datei „docker-compose.override.yml“ erkennen können, unterscheiden sich diese API-Gateway-Container außerdem nur durch die Ocelot-Konfigurationsdatei. Diese Datei ist für jeden Dienstcontainer anders, und sie wird bei Laufzeit über ein Docker-Volume angegeben.</span><span class="sxs-lookup"><span data-stu-id="22245-203">Additionally, as you can see in the following docker-compose.override.yml file, the only difference between those API Gateway containers is the Ocelot configuration file, which is different for each service container and it's specified at runtime through a Docker volume.</span></span>

```yml
mobileshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5200:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Shopping/apigw:/app/configuration

mobilemarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5201:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Marketing/apigw:/app/configuration

webshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5202:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Shopping/apigw:/app/configuration

webmarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5203:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Marketing/apigw:/app/configuration
```

<span data-ttu-id="22245-204">Aufgrund dieses vorherigen Codes und wie im Visual Studio-Explorer weiter veranschaulicht wird, ist zum Definieren der einzelnen Business/BFF-API-Gateways nur eine configuration.json-Datei erforderlich, da die vier API-Gateways auf demselben Docker-Image basieren.</span><span class="sxs-lookup"><span data-stu-id="22245-204">Because of that previous code, and as shown in the Visual Studio Explorer below, the only file needed to define each specific business/BFF API Gateway is just a configuration.json file, because the four API Gateways are based on the same Docker image.</span></span>

![Der einzige Unterschied zwischen allen API-Gateways ist die jeweils eigene „configuration.json“-Datei.](./media/image34.png)

<span data-ttu-id="22245-206">**Abbildung 6-34**.</span><span class="sxs-lookup"><span data-stu-id="22245-206">**Figure 6-34**.</span></span> <span data-ttu-id="22245-207">Zum Definieren der einzelnen API-Gateways/BFF mit Ocelot ist nur eine Konfigurationsdatei erforderlich.</span><span class="sxs-lookup"><span data-stu-id="22245-207">The only file needed to define each API Gateway / BFF with Ocelot is a configuration file</span></span>

<span data-ttu-id="22245-208">Wenn das API-Gateway in mehrere API-Gateways aufgeteilt wird, können verschiedene Entwicklungsteams, die sich auf unterschiedliche Teilmengen von Microservices konzentrieren, ihre eigenen API-Gateways mithilfe von unabhängigen Ocelot-Konfigurationsdateien verwalten.</span><span class="sxs-lookup"><span data-stu-id="22245-208">By splitting the API Gateway into multiple API Gateways, different development teams focusing on different subsets of microservices can manage their own API Gateways by using independent Ocelot configuration files.</span></span> <span data-ttu-id="22245-209">Zudem können sie gleichzeitig dasselbe Ocelot-Docker-Image wiederverwenden.</span><span class="sxs-lookup"><span data-stu-id="22245-209">Plus, at the same time they can reuse the same Ocelot Docker image.</span></span>

<span data-ttu-id="22245-210">Wenn Sie nun beim Öffnen der Projektmappe „eShopOnContainers-ServicesAndWebApps.sln“ oder beim Ausführen von „docker-compose up“ eShopOnContainers mit den API-Gateways ausführen (standardmäßig in VS enthalten), werden die folgenden Beispielrouten ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="22245-210">Now, if you run eShopOnContainers with the API Gateways (included by default in VS when opening eShopOnContainers-ServicesAndWebApps.sln solution or if running “docker-compose up”), the following sample routes will be performed.</span></span>

<span data-ttu-id="22245-211">Beim Aufrufen der vom API-Gateway „webshoppingapigw“ unterstützten Upstream-URL `http://localhost:5202/api/v1/c/catalog/items/2/` erhalten Sie beispielsweise dasselbe Ergebnis von der internen Downstream-URL `http://catalog.api/api/v1/2` im Docker-Host, als in dem folgenden Browser zu sehen ist.</span><span class="sxs-lookup"><span data-stu-id="22245-211">For instance, when visiting the upstream URL `http://localhost:5202/api/v1/c/catalog/items/2/` served by the webshoppingapigw API Gateway, you get the same result from the internal Downstream URL `http://catalog.api/api/v1/2` within the Docker host, as in the following browser.</span></span>

![Browseransicht einer Antwort von „Catalog.api“ über das API-Gateway.](./media/image35.png)

<span data-ttu-id="22245-213">**Abbildung 6-35**.</span><span class="sxs-lookup"><span data-stu-id="22245-213">**Figure 6-35**.</span></span> <span data-ttu-id="22245-214">Zugriff auf einen Microservice über eine vom API-Gateway bereitgestellten URL</span><span class="sxs-lookup"><span data-stu-id="22245-214">Accessing a microservice through a URL provided by the API Gateway</span></span>

<span data-ttu-id="22245-215">Wenn Sie – weil „catalog.api“ eine interne DNS-Auflösung im Docker-Host (für die Dienstermittlung sind „docker-compose“-Dienstnamen verantwortlich) ist – zum Testen oder Debuggen ohne Umweg über das API-Gateway direkt auf den Docker-Container „Catalog“ (nur in der Entwicklungsumgebung) zugreifen möchten, haben Sie nur die Möglichkeit, über den in der Datei „docker-compose.override.yml“ veröffentlichten externen Port auf diesen Container zuzugreifen. Diese Datei wird nur für Entwicklungstests (wie `http://localhost:5101/api/v1/Catalog/items/1` im folgenden Browser) bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="22245-215">Because of testing or debugging reasons, if you wanted to directly access to the Catalog Docker container (only at the development environment) without passing through the API Gateway, since 'catalog.api' is a DNS resolution internal to the Docker host (service discovery handled by docker-compose service names), the only way to directly access the container is through the external port published in the docker-compose.override.yml, which is provided only for development tests, such as `http://localhost:5101/api/v1/Catalog/items/1` in the following browser.</span></span>

![Browseransicht einer Antwort von „Catalog.api“, die direkt an die „Catalog.api“ geleitet wird und die identisch ist mit der Antwort über das API-Gateway.](./media/image36.png)

<span data-ttu-id="22245-217">**Abbildung 6-36**.</span><span class="sxs-lookup"><span data-stu-id="22245-217">**Figure 6-36**.</span></span> <span data-ttu-id="22245-218">Direktzugriff auf einen Microservice zum Testen</span><span class="sxs-lookup"><span data-stu-id="22245-218">Direct access to a microservice for testing purposes</span></span>

<span data-ttu-id="22245-219">Die Anwendung ist jedoch so konfiguriert, dass sie auf alle Microservices über das API-Gateway zugreift und nicht über die direkten „Portverknüpfungen“.</span><span class="sxs-lookup"><span data-stu-id="22245-219">But the application is configured so it accesses all the microservices through the API Gateways, not though the direct port “shortcuts”.</span></span>

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a><span data-ttu-id="22245-220">Das Gateway-Aggregationsmuster in eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="22245-220">The Gateway aggregation pattern in eShopOnContainers</span></span>

<span data-ttu-id="22245-221">Wie bereits erwähnt, bieten benutzerdefinierte Dienste eine flexible Möglichkeit, Anforderungsaggregationen nach Code zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="22245-221">As introduced previously, a flexible way to implement requests aggregation is with custom services, by code.</span></span> <span data-ttu-id="22245-222">Anforderungsaggregationen können auch mit dem [Feature für Anforderungsaggregationen in Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation) implementiert werden. Dieses Feature ist jedoch möglicherweise weniger flexibel.</span><span class="sxs-lookup"><span data-stu-id="22245-222">You could also implement request aggregation with the [Request Aggregation feature in Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), but it might not be as flexible as you need.</span></span> <span data-ttu-id="22245-223">Daher wurde zum Implementieren von Aggregationen in eShopOnContainers für jeden Aggregator ein eigener ASP.NET Core Web-API-Dienst ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="22245-223">Therefore, the selected way to implement aggregation in eShopOnContainers is with an explicit ASP.NET Core Web API services for each aggregator.</span></span>

<span data-ttu-id="22245-224">Diesem Konzept zufolge ist die Abbildung zur API-Gatewayzusammensetzung in Wirklichkeit und unter Berücksichtigung der Aggregatordienste, die in der vereinfachten globalen Architektur weiter oben nicht dargestellt sind, etwas umfassender.</span><span class="sxs-lookup"><span data-stu-id="22245-224">According to that approach, the API Gateway composition diagram is in reality a bit more extended when considering the aggregator services that are not shown in the simplified global architecture diagram shown previously.</span></span>

<span data-ttu-id="22245-225">In der folgenden Abbildung ist ferner zu erkennen, wie die Aggregatordienste die jeweiligen API-Gateways nutzen.</span><span class="sxs-lookup"><span data-stu-id="22245-225">In the following diagram, you can also see how the aggregator services work with their related API Gateways.</span></span>

![eShopOnContainers-Architektur mit Aggregatordiensten.](./media/image37.png)

<span data-ttu-id="22245-227">**Abbildung 6-37**.</span><span class="sxs-lookup"><span data-stu-id="22245-227">**Figure 6-37**.</span></span> <span data-ttu-id="22245-228">eShopOnContainers-Architektur mit Aggregatordiensten</span><span class="sxs-lookup"><span data-stu-id="22245-228">eShopOnContainers architecture with aggregator services</span></span>

<span data-ttu-id="22245-229">Wenn wir den Geschäftsbereich „Shopping“ in der folgenden Abbildung genauer betrachten, erkennen Sie, dass das hohe Kommunikationsaufkommen der Client-Apps mit den Microservices reduziert wird, wenn die Aggregatordienste in den API-Gateways verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="22245-229">Zooming in further, on the “Shopping” business area in the following image, you can see that chattiness between the client apps and the microservices is reduced when using the aggregator services in the API Gateways.</span></span>

![Die detaillierte Darstellung der eShopOnContainers-Architektur, speziell der Aggregatordienste, zeigt das „Zusammenstellen“ einer Antwort, indem die Antworten verschiedener Microservices „zusammengefügt“ werden, um das Kommunikationsaufkommen mit dem End-Client zu reduzieren.](./media/image38.png)

<span data-ttu-id="22245-231">**Abbildung 6-38**.</span><span class="sxs-lookup"><span data-stu-id="22245-231">**Figure 6-38**.</span></span> <span data-ttu-id="22245-232">Größere Darstellung der Aggregatordienste</span><span class="sxs-lookup"><span data-stu-id="22245-232">Zoom in vision of the Aggregator services</span></span>

<span data-ttu-id="22245-233">Wie Sie sehen, wird das Ganze recht komplex, wenn in der Abbildung die möglichen Anforderungen von den API-Gateways dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="22245-233">You can notice how when the diagram shows the possible requests coming from the API Gateways it can get pretty complex.</span></span> <span data-ttu-id="22245-234">Sie können sehen, wie die blauen Pfeile aus der Sicht von Client-Apps bei Verwendung des Aggregatormusters deutlich vereinfacht wurden, indem das Kommunikationsaufkommen und die Latenz in der Kommunikation reduziert wurden. Dadurch wird insbesondere die Benutzerfreundlichkeit für die Remote-Apps (mobile Apps und SPA-Apps) erheblich verbessert.</span><span class="sxs-lookup"><span data-stu-id="22245-234">Although you can see how the arrows in blue would be simplified, from a client apps perspective, when using the aggregator pattern by reducing chattiness and latency in the communication, ultimately significantly improving the user experience for the remote apps (mobile and SPA apps), especially.</span></span>

<span data-ttu-id="22245-235">Beim Geschäftsbereich „Marketing“ und den entsprechenden Microservices geht es um einen sehr einfachen Anwendungsfall. Daher mussten keine Aggregatoren verwendet werden. Bei Bedarf wäre dies jedoch möglich.</span><span class="sxs-lookup"><span data-stu-id="22245-235">In the case of the “Marketing” business area and microservices, it is a very simple use case so there was no need to use aggregators, but it could also be possible, if needed.</span></span>

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a><span data-ttu-id="22245-236">Authentifizierung und Autorisierung in Ocelot-API-Gateways</span><span class="sxs-lookup"><span data-stu-id="22245-236">Authentication and authorization in Ocelot API Gateways</span></span>

<span data-ttu-id="22245-237">In einem Ocelot-API-Gateway können Sie den Authentifizierungsdienst wie etwa einen ASP.NET Core Web-API-Dienst mithilfe von [IdentityServer](https://identityserver.io/) zur Bereitstellung des Authentifizierungstokens innerhalb oder außerhalb des API-Gateways platzieren.</span><span class="sxs-lookup"><span data-stu-id="22245-237">In an Ocelot API Gateway you can sit the authentication service, such as an ASP.NET Core Web API service using [IdentityServer](https://identityserver.io/) providing the auth token, either out or inside the API Gateway.</span></span>

<span data-ttu-id="22245-238">Da eShopOnContainers mehrere API-Gateways mit Grenzen verwendet, die auf BFF und Geschäftsbereichen basieren, wird der Dienst „Identity/Auth“ außerhalb des API-Gateways platziert (in der folgenden Abbildung gelb hervorgehoben).</span><span class="sxs-lookup"><span data-stu-id="22245-238">Since eShopOnContainers is using multiple API Gateways with boundaries based on BFF and business areas, the Identity/Auth service is left out of the API Gateways, as highlighted in yellow in the following diagram.</span></span>

![In dem folgenden Diagramm der eShopOnContainers-Architektur ist der Microservice „Identity“ unterhalb des API-Gateways zu sehen.](./media/image39.png)

<span data-ttu-id="22245-240">**Abbildung 6-39**.</span><span class="sxs-lookup"><span data-stu-id="22245-240">**Figure 6-39**.</span></span> <span data-ttu-id="22245-241">Position des Microservice „Identity“ in eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="22245-241">Position of the Identity service in eShopOnContainers</span></span>

<span data-ttu-id="22245-242">Wie in der folgenden Abbildung zu sehen ist, unterstützt Ocelot auch die Platzierung des Microservice „Identity/Auth“ innerhalb der API-Gateway-Grenze.</span><span class="sxs-lookup"><span data-stu-id="22245-242">However, Ocelot also supports sitting the Identity/Auth microservice within the API Gateway boundary, as in this other diagram.</span></span>

![Authentifizierung Microservice „Identity“ unterhalb der API-Gateway (AG): 1) AG fordert ein Authentifizierungstoken vom Microservice „Identity“, 2) Microservice „Identity“ gibt das Token zurück an AG, 3-4) AG fordert vom Microservice die Verwendung des Authentifizierungstokens.](./media/image40.png)

<span data-ttu-id="22245-244">**Abbildung 6-40**.</span><span class="sxs-lookup"><span data-stu-id="22245-244">**Figure 6-40**.</span></span> <span data-ttu-id="22245-245">Authentifizierung in Ocelot</span><span class="sxs-lookup"><span data-stu-id="22245-245">Authentication in Ocelot</span></span>

<span data-ttu-id="22245-246">Da bei der Anwendung eShopOnContainers das API-Gateway in mehrere BFF-API-Gateways (Backend for Frontend) und Geschäftsbereich-API-Gateways aufgeteilt ist, wäre eine andere Möglichkeit gewesen, ein zusätzliches API-Gateway für übergreifende Belange zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="22245-246">Because eShopOnContainers application has split the API Gateway into multiple BFF (Backend for Frontend) and business areas API Gateways, another option would had been to create an additional API Gateway for cross-cutting concerns.</span></span> <span data-ttu-id="22245-247">Diese Option wäre in einer komplexeren, auf Microservices basierenden Architektur mit mehreren Microservices für übergreifende Belange angemessen.</span><span class="sxs-lookup"><span data-stu-id="22245-247">That choice would be fair in a more complex microservice based architecture with multiple cross-cutting concerns microservices.</span></span> <span data-ttu-id="22245-248">Da es in eShopOnContainers nur einen übergreifenden Belang gibt, wurde entschieden, der Einfachheit halber aus dem Bereich des API-Gateways nur den Sicherheitsdienst zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="22245-248">Since there's only one cross-cutting concern in eShopOnContainers, it was decided to just handle the security service out of the API Gateway realm, for simplicity’s sake.</span></span>

<span data-ttu-id="22245-249">Wenn die App auf der API-Gateway-Ebene geschützt wird, wird bei Verwendung eines geschützten Microservice auf jeden Fall zuerst das Authentifizierungsmodul des Ocelot-API-Gateways aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="22245-249">In any case, if the app is secured at the API Gateway level, the authentication module of the Ocelot API Gateway is visited at first when trying to use any secured microservice.</span></span> <span data-ttu-id="22245-250">Dieses leitet die HTTP-Anforderung zum Aufrufen des Microservice „Identity“ oder „Auth“ um, um so das Zugriffstoken abzurufen, damit die geschützten Dienste mit dem Zugriffstoken aufgerufen werden können.</span><span class="sxs-lookup"><span data-stu-id="22245-250">That re-directs the HTTP request to visit the Identity or auth microservice to get the access token so you can visit the protected services with the access_token.</span></span>

<span data-ttu-id="22245-251">Dienste werden auf der API-Gateway-Ebene mittels Authentifizierung geschützt, indem „AuthenticationProviderKey“ in den entsprechenden Einstellungen in der Datei „configuration.json“ festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="22245-251">The way you secure with authentication any service at the API Gateway level is by setting the AuthenticationProviderKey in its related settings at the configuration.json.</span></span>

```json
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }
```

<span data-ttu-id="22245-252">Wenn Ocelot ausgeführt wird, wird bei den ReRoutes „AuthenticationOptions.AuthenticationProviderKey“ geprüft, ob für den angegebenen Schlüssel ein Authentifizierungsanbieter registriert wurde.</span><span class="sxs-lookup"><span data-stu-id="22245-252">When Ocelot runs, it will look at the Re-Routes AuthenticationOptions.AuthenticationProviderKey and check that there is an Authentication Provider registered with the given key.</span></span> <span data-ttu-id="22245-253">Ist kein Schlüssel vorhanden, wird Ocelot nicht gestartet.</span><span class="sxs-lookup"><span data-stu-id="22245-253">If there isn't, then Ocelot will not start up.</span></span> <span data-ttu-id="22245-254">Ist ein Schlüssel vorhanden, wird der entsprechende Anbieter beim Ausführen von ReRoute verwendet.</span><span class="sxs-lookup"><span data-stu-id="22245-254">If there is, then the ReRoute will use that provider when it executes.</span></span>

<span data-ttu-id="22245-255">Da der Ocelot-Webhost mit `authenticationProviderKey = "IdentityApiKey"` konfiguriert wurde, ist immer dann eine Authentifizierung erforderlich, wenn dieser Dienst Anforderungen ohne Authentifizierungstoken aufweist.</span><span class="sxs-lookup"><span data-stu-id="22245-255">Because the Ocelot WebHost is configured with the `authenticationProviderKey = "IdentityApiKey"`, that will require authentication whenever that service has any requests without any auth token.</span></span>

```csharp
namespace OcelotApiGw
{
    public class Startup
    {
        private readonly IConfiguration _cfg;

        public Startup(IConfiguration configuration) => _cfg = configuration;

        public void ConfigureServices(IServiceCollection services)
        {
            var identityUrl = _cfg.GetValue<string>("IdentityUrl");
            var authenticationProviderKey = "IdentityApiKey";
                         //…
            services.AddAuthentication()
                .AddJwtBearer(authenticationProviderKey, x =>
                {
                    x.Authority = identityUrl;
                    x.RequireHttpsMetadata = false;
                    x.TokenValidationParameters = new Microsoft.IdentityModel.Tokens.TokenValidationParameters()
                    {
                        ValidAudiences = new[] { "orders", "basket", "locations", "marketing", "mobileshoppingagg", "webshoppingagg" }
                    };
                });
            //...
        }
    }
}
```

<span data-ttu-id="22245-256">Ferner müssen Sie wie beim folgenden Controller des Microservice „Basket“ die Autorisierung mit dem Attribut „[Authorize]“ für alle Ressourcen festlegen, auf die zugegriffen werden soll, wie etwa für die Microservices.</span><span class="sxs-lookup"><span data-stu-id="22245-256">Then, you also need to set authorization with the [Authorize] attribute on any resource to be accessed like the microservices, such as in the following Basket microservice controller.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class BasketController : Controller
    {
      //...
    }
}
```

<span data-ttu-id="22245-257">„ValidAudiences“ wie „basket“ sind wie im folgenden Code mit der in den einzelnen Microservices mit `AddJwtBearer()` in „ConfigureServices()“ der Startup-Klasse definierten Zielgruppe verknüpft.</span><span class="sxs-lookup"><span data-stu-id="22245-257">The ValidAudiences such as “basket” are correlated with the audience defined in each microservice with `AddJwtBearer()` at the ConfigureServices() of the Startup class, such as in the code below.</span></span>

```csharp
// prevent from mapping "sub" claim to nameidentifier.
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();

var identityUrl = Configuration.GetValue<string>("IdentityUrl");

services.AddAuthentication(options =>
{
    options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
    options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;

}).AddJwtBearer(options =>
{
    options.Authority = identityUrl;
    options.RequireHttpsMetadata = false;
    options.Audience = "basket";
});
```

<span data-ttu-id="22245-258">Wenn Sie auf einen geschützten Microservice wie „Basket“ mit einer ReRoute-URL basierend auf einen API-Gateway wie `http://localhost:5202/api/v1/b/basket/1` zugreifen und kein gültiges Token angeben, erhalten Sie die Fehlermeldung „401 – Nicht autorisiert.“.</span><span class="sxs-lookup"><span data-stu-id="22245-258">If you try to access any secured microservice, like the Basket microservice with a Re-Route URL based on the API Gateway like `http://localhost:5202/api/v1/b/basket/1`, then you’ll get a 401 Unauthorized unless you provide a valid token.</span></span> <span data-ttu-id="22245-259">Wenn eine ReRoute-URL jedoch authentifiziert wird, ruft Ocelot das damit (mit der internen Microservice-URL) verbundene Downstreamschema auf.</span><span class="sxs-lookup"><span data-stu-id="22245-259">On the other hand, if a Re-Route URL is authenticated, Ocelot will invoke whatever downstream scheme is associated with it (the internal microservice URL).</span></span>

<span data-ttu-id="22245-260">**Autorisierung auf der ReRoute-Ebene von Ocelot.**</span><span class="sxs-lookup"><span data-stu-id="22245-260">**Authorization at Ocelot’s ReRoutes tier.**</span></span>  <span data-ttu-id="22245-261">Ocelot unterstützt die anspruchsbasierte Autorisierung, die nach der Authentifizierung ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="22245-261">Ocelot supports claims-based authorization evaluated after the authentication.</span></span> <span data-ttu-id="22245-262">Sie können die Autorisierung auf Routenebene festlegen, indem Sie die folgenden Zeilen zur ReRoute-Konfiguration hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="22245-262">You set the authorization at a route level by adding the following lines to the ReRoute configuration.</span></span>

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

<span data-ttu-id="22245-263">Wenn die Autorisierungsmiddleware in diesem Beispiel aufgerufen wird, erkennt Ocelot, ob im Benutzer der Anspruchstyp „UserType“ im Token enthalten ist und ob der Wert dieses Anspruchs „employee“ lautet.</span><span class="sxs-lookup"><span data-stu-id="22245-263">In that example, when the authorization middleware is called, Ocelot will find if the user has the claim type 'UserType' in the token and if the value of that claim is 'employee'.</span></span> <span data-ttu-id="22245-264">Ist dies nicht der Fall, wird der Benutzer nicht autorisiert und die Antwort lautet „403 Verboten“.</span><span class="sxs-lookup"><span data-stu-id="22245-264">If it isn’t, then the user will not be authorized and the response will be 403 forbidden.</span></span>

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a><span data-ttu-id="22245-265">Verwenden von Kubernetes Ingress und Ocelot-API-Gateways</span><span class="sxs-lookup"><span data-stu-id="22245-265">Using Kubernetes Ingress plus Ocelot API Gateways</span></span>

<span data-ttu-id="22245-266">Wenn Sie Kubernetes (wie etwa in einem Azure Kubernetes Service-Cluster) verwenden, führen Sie in der Regel alle HTTP-Anforderungen über die [Kubernetes Ingress-Ebene](https://kubernetes.io/docs/concepts/services-networking/ingress/) basierend auf *Nginx* zusammen.</span><span class="sxs-lookup"><span data-stu-id="22245-266">When using Kubernetes (like in an Azure Kubernetes Service cluster), you usually unify all the HTTP requests through the [Kubernetes Ingress tier](https://kubernetes.io/docs/concepts/services-networking/ingress/) based on *Nginx*.</span></span>

<span data-ttu-id="22245-267">Wenn Sie in Kubernetes kein Ingress-Konzept verwenden, können die IPs Ihrer Dienste und Pods nur vom Clusternetzwerk geroutet werden.</span><span class="sxs-lookup"><span data-stu-id="22245-267">In Kubernetes, if you don’t use any ingress approach, then your services and pods have IPs only routable by the cluster network.</span></span>

<span data-ttu-id="22245-268">Wenn jedoch ein Ingress-Konzept erkennbar ist, ist zwischen dem Internet und Ihren Diensten (und Ihren API-Gateways) eine mittlere Ebene vorhanden, die als Reverseproxy dient.</span><span class="sxs-lookup"><span data-stu-id="22245-268">But if you use an ingress approach, you'll have a middle tier between the Internet and your services (including your API Gateways), acting as a reverse proxy.</span></span>

<span data-ttu-id="22245-269">Ingress ist als eine Sammlung von Regeln definiert, die es eingehenden Verbindungen ermöglichen, die Clusterdienste zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="22245-269">As a definition, an Ingress is a collection of rules that allow inbound connections to reach the cluster services.</span></span> <span data-ttu-id="22245-270">Ingress wird normalerweise konfiguriert, um Diensten extern erreichbare URLs, Lastausgleich für den Datenverkehr, SSL-Terminierung usw. bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="22245-270">An ingress is usually configured to provide services externally reachable URLs, load balance traffic, SSL termination and more.</span></span> <span data-ttu-id="22245-271">Benutzer fordern Ingress an, indem sie die Ingress-Ressource an den API-Server senden.</span><span class="sxs-lookup"><span data-stu-id="22245-271">Users request ingress by POSTing the Ingress resource to the API server.</span></span>

<span data-ttu-id="22245-272">Wenn Sie in eShopOnContainers lokal entwickeln und nur Ihren Entwicklungscomputer als Docker-Host verwenden, benötigen Sie Ingress nicht, sondern nur die API-Gateways.</span><span class="sxs-lookup"><span data-stu-id="22245-272">In eShopOnContainers, when developing locally and using just your development machine as the Docker host, you are not using any ingress but only the multiple API Gateways.</span></span>

<span data-ttu-id="22245-273">Wenn Sie dagegen eine Produktionsumgebung basierend auf Kubernetes als Ziel festlegen, wird Ingress von eShopOnContainers vor die API-Gateways geschaltet.</span><span class="sxs-lookup"><span data-stu-id="22245-273">However, when targeting a “production” environment based on Kubernetes, eShopOnContainers is using an ingress in front of the API gateways.</span></span> <span data-ttu-id="22245-274">Auf diese Weise rufen die Clients weiterhin dieselbe Basis-URL auf, die Anforderungen werden jedoch an die API-Gateways oder BFF weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="22245-274">That way, the clients still call the same base URL but the requests are routed to multiple API Gateways or BFF.</span></span>

<span data-ttu-id="22245-275">API-Gateways sind Front-Ends oder Fassaden, die nur die Dienste, nicht jedoch die Webanwendungen bereitstellen, die in der Regel außerhalb deren Bereich liegen.</span><span class="sxs-lookup"><span data-stu-id="22245-275">Note that API Gateways are front-ends or façades surfacing only the services but not the web applications that are usually out of their scope.</span></span> <span data-ttu-id="22245-276">Zudem können die API-Gateways bestimmte interne Microservices verbergen.</span><span class="sxs-lookup"><span data-stu-id="22245-276">In addition, the API Gateways might hide certain internal microservices.</span></span>

<span data-ttu-id="22245-277">Ingress leitet dagegen nur HTTP-Anforderungen um und versucht nicht, Microservices oder Webanwendungen zu verbergen.</span><span class="sxs-lookup"><span data-stu-id="22245-277">The ingress, however, is just redirecting HTTP requests but not trying to hide any microservice or web app.</span></span>

<span data-ttu-id="22245-278">Eine Ingress-Nginx-Ebene in Kubernetes vor den Webanwendungen sowie mehrere Ocelot-API-Gateways/BFFs wie in der folgenden Abbildung ist die ideale Architektur.</span><span class="sxs-lookup"><span data-stu-id="22245-278">Having an ingress Nginx tier in Kubernetes in front of the web applications plus the several Ocelot API Gateways / BFF is the ideal architecture, as shown in the following diagram.</span></span>

![Kubernetes Ingress dient als Reverseproxy für den gesamten Datenverkehr zur App. Dies gilt auch für Web-Apps, die normalerweise außerhalb des API-Gateway-Bereichs liegen.](./media/image41.png)

<span data-ttu-id="22245-280">**Abbildung 6-41**.</span><span class="sxs-lookup"><span data-stu-id="22245-280">**Figure 6-41**.</span></span> <span data-ttu-id="22245-281">Die Ingress-Ebene in eShopOnContainers bei Bereitstellung in Kubernetes</span><span class="sxs-lookup"><span data-stu-id="22245-281">The ingress tier in eShopOnContainers when deployed into Kubernetes</span></span>

<span data-ttu-id="22245-282">Wenn Sie eShopOnContainers in Kubernetes bereitstellen, werden nur wenige Dienste oder Endpunkte über _ingress_ verfügbar gemacht. Hierbei handelt es sich im Wesentlichen um die folgende Liste mit Postfixes in den URLs:</span><span class="sxs-lookup"><span data-stu-id="22245-282">When you deploy eShopOnContainers into Kubernetes, it exposes just a few services or endpoints via _ingress_, basically the following list of postfixes on the URLs:</span></span>

- <span data-ttu-id="22245-283">`/` für die SPA-Clientwebanwendung</span><span class="sxs-lookup"><span data-stu-id="22245-283">`/` for the client SPA web application</span></span>
- <span data-ttu-id="22245-284">`/webmvc` für die MVC-Clientwebanwendung</span><span class="sxs-lookup"><span data-stu-id="22245-284">`/webmvc` for the client MVC web application</span></span>
- <span data-ttu-id="22245-285">`/webstatus` für die Clientwebanwendung, zeigt den Status/Integritätsprüfungen an</span><span class="sxs-lookup"><span data-stu-id="22245-285">`/webstatus` for the client web app showing the status/healthchecks</span></span>
- <span data-ttu-id="22245-286">`/webshoppingapigw` für die BFF- und „Shopping“-Webgeschäftsprozesse</span><span class="sxs-lookup"><span data-stu-id="22245-286">`/webshoppingapigw` for the web BFF and shopping business processes</span></span>
- <span data-ttu-id="22245-287">`/webmarketingapigw` für die BFF- und „Marketing“-Webgeschäftsprozesse</span><span class="sxs-lookup"><span data-stu-id="22245-287">`/webmarketingapigw` for the web BFF and marketing business processes</span></span>
- <span data-ttu-id="22245-288">`/mobileshoppingapigw` für die mobilen BFF- und „Shopping“-Geschäftsprozesse</span><span class="sxs-lookup"><span data-stu-id="22245-288">`/mobileshoppingapigw` for the mobile BFF and shopping business processes</span></span>
- <span data-ttu-id="22245-289">`/mobilemarketingapigw` für die mobilen BFF- und „Marketing“-Geschäftsprozesse</span><span class="sxs-lookup"><span data-stu-id="22245-289">`/mobilemarketingapigw` for the mobile BFF and marketing business processes</span></span>

<span data-ttu-id="22245-290">Bei der Bereitstellung für Kubernetes verwendet jedes Ocelot-API-Gateway für jeden _Pod_, der die API-Gateways ausführt, eine andere configuration.json-Datei.</span><span class="sxs-lookup"><span data-stu-id="22245-290">When deploying to Kubernetes, each Ocelot API Gateway is using a different “configuration.json” file for each _pod_ running the API Gateways.</span></span> <span data-ttu-id="22245-291">Diese configuration.json-Dateien werden bereitgestellt, indem ein Volume (ursprünglich mit dem Skript „deploy.ps1“) eingebunden wird, das auf einer Kubernetes-_Konfigurationszuordnung_ mit dem Namen „ocelot“ basiert.</span><span class="sxs-lookup"><span data-stu-id="22245-291">Those “configuration.json” files are provided by mounting (originally with the deploy.ps1 script) a volume created based on a Kubernetes _config map_ named ‘ocelot’.</span></span> <span data-ttu-id="22245-292">Jeder Container bindet die entsprechende Konfigurationsdatei in den Containerordner namens `/app/configuration` ein.</span><span class="sxs-lookup"><span data-stu-id="22245-292">Each container mounts its related configuration file in the container’s folder named `/app/configuration`.</span></span>

<span data-ttu-id="22245-293">In den Quellcodedateien von eShopOnContainers befinden sich die ursprünglichen configuration.json-Dateien im Ordner `k8s/ocelot/`.</span><span class="sxs-lookup"><span data-stu-id="22245-293">In the source code files of eShopOnContainers, the original “configuration.json” files can be found within the `k8s/ocelot/` folder.</span></span> <span data-ttu-id="22245-294">Für jedes BFF/API-Gateway gibt es eine Datei.</span><span class="sxs-lookup"><span data-stu-id="22245-294">There’s one file for each BFF/APIGateway.</span></span>

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a><span data-ttu-id="22245-295">Weitere übergreifende Features in einem Ocelot-API-Gateway</span><span class="sxs-lookup"><span data-stu-id="22245-295">Additional cross-cutting features in an Ocelot API Gateway</span></span>

<span data-ttu-id="22245-296">Bei Verwendung eines Ocelot-API-Gateways gibt es weitere wichtige Features zu erforschen und zu verwenden. Diese werden unter den folgenden Links beschrieben.</span><span class="sxs-lookup"><span data-stu-id="22245-296">There are other important features to research and use, when using an Ocelot API Gateway, described in the following links.</span></span>

- <span data-ttu-id="22245-297">**Dienstermittlung auf Clientseite mit Integration von Ocelot in Consul oder Eureka** </span><span class="sxs-lookup"><span data-stu-id="22245-297">**Service discovery in the client side integrating Ocelot with Consul or Eureka** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- <span data-ttu-id="22245-298">**Zwischenspeichern auf der API-Gateway-Ebene** </span><span class="sxs-lookup"><span data-stu-id="22245-298">**Caching at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- <span data-ttu-id="22245-299">**Protokollieren auf der API-Gateway-Ebene** </span><span class="sxs-lookup"><span data-stu-id="22245-299">**Logging at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- <span data-ttu-id="22245-300">**Quality of Service (Wiederholungen und Schaltkreisunterbrecher) auf der API-Gateway-Ebene** </span><span class="sxs-lookup"><span data-stu-id="22245-300">**Quality of Service (Retries and Circuit breakers) at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- <span data-ttu-id="22245-301">**Bandbreitenbegrenzung** </span><span class="sxs-lookup"><span data-stu-id="22245-301">**Rate limiting** </span></span>\
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> <span data-ttu-id="22245-302">[Zurück](background-tasks-with-ihostedservice.md)
> [Weiter](../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="22245-302">[Previous](background-tasks-with-ihostedservice.md)
[Next](../microservice-ddd-cqrs-patterns/index.md)</span></span>