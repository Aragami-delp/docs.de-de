---
title: Zusammenfassung
description: Hier finden Sie eine Zusammenfassung der wichtigsten Schlussfolgerungen aus dem Leitfaden zum Entwerfen von Cloud-Native .net-apps für Azure.
ms.date: 04/29/2020
ms.openlocfilehash: 97f20771aae73ed88d2dadefa7ba89d64eb62fcd
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82899707"
---
# <a name="summary"></a><span data-ttu-id="7ea61-103">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="7ea61-103">Summary</span></span>

<span data-ttu-id="7ea61-104">Zusammenfassend sind die folgenden wichtigen Schlussfolgerungen in diesem Handbuch aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="7ea61-104">In summary, here are important conclusions from this guide:</span></span>

- <span data-ttu-id="7ea61-105">**Cloud-Native** ist das Entwerfen moderner Anwendungen, die eine schnelle Änderung, große Skalierbarkeit und Resilienz in modernen, dynamischen Umgebungen wie öffentlichen, privaten und Hybriden Clouds umfassen.</span><span class="sxs-lookup"><span data-stu-id="7ea61-105">**Cloud-native** is about designing modern applications that embrace rapid change, large scale, and resilience, in modern, dynamic environments such as public, private, and hybrid clouds.</span></span>

- <span data-ttu-id="7ea61-106">Die \*\* [Cloud Native Computing Foundation](https://www.cncf.io/) (cncf)\*\* ist ein einflussreiches Open-Source-Konsortium von über 300 großen Unternehmen.</span><span class="sxs-lookup"><span data-stu-id="7ea61-106">The **[Cloud Native Computing Foundation](https://www.cncf.io/) (CNCF)** is an influential open-source consortium of over 300 major corporations.</span></span> <span data-ttu-id="7ea61-107">Er ist dafür verantwortlich, die Übernahme von Cloud-Native Computing über Technologie-und cloudstapel hinweg zu fördern.</span><span class="sxs-lookup"><span data-stu-id="7ea61-107">It's responsible for driving the adoption of cloud-native computing across technology and cloud stacks.</span></span>

- <span data-ttu-id="7ea61-108">**Cncf-Richtlinien** empfehlen, dass cloudnative Anwendungen sechs wichtige Säulen akzeptieren, wie in Abbildung 12-1 dargestellt:</span><span class="sxs-lookup"><span data-stu-id="7ea61-108">**CNCF guidelines** recommend that that cloud-native applications embrace six important pillars as shown in Figure 12-1:</span></span>

  ![In der Cloud Native grundlegende Säulen](./media/cloud-native-foundational-pillars.png)

  <span data-ttu-id="7ea61-110">**Abbildung 12-1**.</span><span class="sxs-lookup"><span data-stu-id="7ea61-110">**Figure 12-1**.</span></span> <span data-ttu-id="7ea61-111">In der Cloud Native grundlegende Säulen</span><span class="sxs-lookup"><span data-stu-id="7ea61-111">Cloud-native foundational pillars</span></span>

- <span data-ttu-id="7ea61-112">Diese cloudbasierten Säulen umfassen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="7ea61-112">These cloud-native pillars include:</span></span>
  - <span data-ttu-id="7ea61-113">Die Cloud und das zugrunde liegende Dienstmodell</span><span class="sxs-lookup"><span data-stu-id="7ea61-113">The cloud and its underlying service model</span></span>
  - <span data-ttu-id="7ea61-114">Moderne Entwurfs Prinzipien</span><span class="sxs-lookup"><span data-stu-id="7ea61-114">Modern design principles</span></span>
  - <span data-ttu-id="7ea61-115">Microservices</span><span class="sxs-lookup"><span data-stu-id="7ea61-115">Microservices</span></span>
  - <span data-ttu-id="7ea61-116">Containerisierung und Container Orchestrierung</span><span class="sxs-lookup"><span data-stu-id="7ea61-116">Containerization and container orchestration</span></span>
  - <span data-ttu-id="7ea61-117">Cloudbasierte Unterstützungsdienste, z. b. Datenbanken und Nachrichten Broker</span><span class="sxs-lookup"><span data-stu-id="7ea61-117">Cloud-based backing services, such as databases and message brokers</span></span>
  - <span data-ttu-id="7ea61-118">Automatisierung, einschließlich Infrastruktur als Code und Code Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="7ea61-118">Automation, including Infrastructure as Code and code deployment</span></span>

- <span data-ttu-id="7ea61-119">**Kubernetes** ist die bevorzugte Hostingumgebung für die meisten cloudbasierten Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="7ea61-119">**Kubernetes** is the hosting environment of choice for most cloud-native applications.</span></span> <span data-ttu-id="7ea61-120">Kleinere, einfache Dienste werden manchmal auf Server losen Plattformen gehostet, wie z. b. Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="7ea61-120">Smaller, simple services are sometimes hosted in serverless platforms, such as Azure Functions.</span></span> <span data-ttu-id="7ea61-121">Bei vielen wichtigen Automatisierungs Features bieten beide Umgebungen eine automatische Skalierung, um schwankende workloadvolumes zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="7ea61-121">Among many key automation features, both environments provide automatic scaling to handle fluctuating workload volumes.</span></span>

- <span data-ttu-id="7ea61-122">Die **Dienst Kommunikation** wird bei der Erstellung einer Cloud-native Anwendung zu einer erheblichen Entwurfs Entscheidung.</span><span class="sxs-lookup"><span data-stu-id="7ea61-122">**Service communication** becomes a significant design decision when constructing a cloud-native application.</span></span> <span data-ttu-id="7ea61-123">Anwendungen stellen in der Regel ein API-Gateway zum Verwalten der Front-End-Client Kommunikation bereit.</span><span class="sxs-lookup"><span data-stu-id="7ea61-123">Applications typically expose an API gateway to manage front-end client communication.</span></span> <span data-ttu-id="7ea61-124">Die Back-End-mikrodienste sind dann bestrebt, miteinander zu kommunizieren, indem asynchrone Kommunikationsmuster implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="7ea61-124">Then backend microservices strive to communicate with each other implementing asynchronous communication patterns, when possible.</span></span>

- <span data-ttu-id="7ea61-125">**GrpC** ist ein modernes Hochleistungs Framework, das das alte RPC-Protokoll (Remote Procedure callage) weiterentwickelt.</span><span class="sxs-lookup"><span data-stu-id="7ea61-125">**gRPC** is a modern, high-performance framework that evolves the age-old remote procedure call (RPC) protocol.</span></span> <span data-ttu-id="7ea61-126">Native Cloud-Anwendungen nutzen häufig GrpC, um das Messaging zwischen Back-End-Diensten zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="7ea61-126">Cloud-native applications often embrace gRPC to streamline messaging between back-end services.</span></span> <span data-ttu-id="7ea61-127">GrpC verwendet http/2 für das Transportprotokoll.</span><span class="sxs-lookup"><span data-stu-id="7ea61-127">gRPC uses HTTP/2 for its transport protocol.</span></span> <span data-ttu-id="7ea61-128">Es kann bis zu 8-mal schneller als die JSON-Serialisierung mit Nachrichten Größen von 60-80% kleiner sein.</span><span class="sxs-lookup"><span data-stu-id="7ea61-128">It can be up to 8x faster than JSON serialization with message sizes 60-80% smaller.</span></span> <span data-ttu-id="7ea61-129">GrpC ist Open Source und wird von der Cloud Native Computing Foundation (cncf) verwaltet.</span><span class="sxs-lookup"><span data-stu-id="7ea61-129">gRPC is open source and managed by the Cloud Native Computing Foundation (CNCF).</span></span>

- <span data-ttu-id="7ea61-130">**Verteilte Daten** sind ein Modell, das häufig von cloudbasierten Anwendungen implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="7ea61-130">**Distributed data** is a model often implemented by cloud-native applications.</span></span> <span data-ttu-id="7ea61-131">Anwendungen trennen Geschäftsfunktionen in kleine, unabhängige microservices.</span><span class="sxs-lookup"><span data-stu-id="7ea61-131">Applications segregate business functionality into small, independent microservices.</span></span> <span data-ttu-id="7ea61-132">Jeder microservice kapselt seine eigenen Abhängigkeiten, Daten und seinen Zustand.</span><span class="sxs-lookup"><span data-stu-id="7ea61-132">Each microservice encapsulates its own dependencies, data, and state.</span></span> <span data-ttu-id="7ea61-133">Das klassische Modell für freigegebene Datenbanken wird zu einer von vielen kleineren Datenbanken weiterentwickelt, die jeweils mit einem-Dienst ausgerichtet sind.</span><span class="sxs-lookup"><span data-stu-id="7ea61-133">The classic shared database model evolves into one of many smaller databases, each aligning with a microservice.</span></span> <span data-ttu-id="7ea61-134">Wenn der Rauch gelöscht wird, werden wir einen Entwurf mit einem `database-per-microservice` Modell erstellen.</span><span class="sxs-lookup"><span data-stu-id="7ea61-134">When the smoke clears, we emerge with a design that exposes a `database-per-microservice` model.</span></span>

- <span data-ttu-id="7ea61-135">**Nein-SQL-Datenbanken** beziehen sich auf nicht relationale Datenspeicher mit hoher Leistung.</span><span class="sxs-lookup"><span data-stu-id="7ea61-135">**No-SQL databases** refer to high-performance, non-relational data stores.</span></span> <span data-ttu-id="7ea61-136">Sie sind in der Benutzerfreundlichkeit, Skalierbarkeit, Resilienz und Verfügbarkeits Merkmalen von Excel.</span><span class="sxs-lookup"><span data-stu-id="7ea61-136">They excel in their ease-of-use, scalability, resilience, and availability characteristics.</span></span> <span data-ttu-id="7ea61-137">Hohe Volumen Dienste, die eine Antwortzeit der untergeordneten Sekunde erfordern, bevorzugen nosql-Datenspeicher.</span><span class="sxs-lookup"><span data-stu-id="7ea61-137">High volume services that require sub second response time favor NoSQL datastores.</span></span> <span data-ttu-id="7ea61-138">Die Verbreitung von nosql-Technologien für verteilte cloudnative Systeme kann nicht überschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="7ea61-138">The proliferation of NoSQL technologies for distributed cloud-native systems can't be overstated.</span></span>

- <span data-ttu-id="7ea61-139">**Newsql** ist eine neue Datenbanktechnologie, die die verteilte Skalierbarkeit von nosql und die Acid-Garantien einer relationalen Datenbank kombiniert.</span><span class="sxs-lookup"><span data-stu-id="7ea61-139">**NewSQL** is an emerging database technology that combines the distributed scalability of NoSQL and the ACID guarantees of a relational database.</span></span> <span data-ttu-id="7ea61-140">Newsql-Datenbanken sind auf Geschäftssysteme ausgerichtet, die große Mengen von Daten in verteilten Umgebungen mit vollständiger Transaktions-/Acid-Konformität verarbeiten müssen.</span><span class="sxs-lookup"><span data-stu-id="7ea61-140">NewSQL databases target business systems that must process high-volumes of data, across distributed environments, with full transactional/ACID compliance.</span></span> <span data-ttu-id="7ea61-141">Die Cloud Native Computing Foundation (cncf) umfasst mehrere newsql-Datenbankprojekte.</span><span class="sxs-lookup"><span data-stu-id="7ea61-141">The Cloud Native Computing Foundation (CNCF) features several NewSQL database projects.</span></span>

- <span data-ttu-id="7ea61-142">**Resilienz** ist die Fähigkeit Ihres Systems, auf Fehler zu reagieren, und bleibt weiterhin funktionsfähig.</span><span class="sxs-lookup"><span data-stu-id="7ea61-142">**Resiliency** is the ability of your system to react to failure and still remain functional.</span></span> <span data-ttu-id="7ea61-143">Cloud-Native Systeme nutzen eine verteilte Architektur, bei der ein Fehler unvermeidlich ist.</span><span class="sxs-lookup"><span data-stu-id="7ea61-143">Cloud-native systems embrace distributed architecture where failure is inevitable.</span></span> <span data-ttu-id="7ea61-144">Anwendungen müssen so erstellt werden, dass Sie elegant auf Fehler reagieren und schnell zu einem voll funktionsfähigen Status zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="7ea61-144">Applications must be constructed to respond elegantly to failure and quickly return to a fully functioning state.</span></span>

- <span data-ttu-id="7ea61-145">**Dienst-Netzen** sind eine konfigurierbare Infrastruktur Schicht mit integrierten Funktionen, um die Dienst Kommunikation und andere übergreifende Herausforderungen zu bewältigen.</span><span class="sxs-lookup"><span data-stu-id="7ea61-145">**Service meshes** are a configurable infrastructure layer with built-in capabilities to handle service communication and other cross-cutting challenges.</span></span> <span data-ttu-id="7ea61-146">Sie entkoppeln die übergreifenden Zuständigkeiten von Ihrem Geschäfts Code.</span><span class="sxs-lookup"><span data-stu-id="7ea61-146">They decouple cross-cutting responsibilities from your business code.</span></span> <span data-ttu-id="7ea61-147">Diese Zuständigkeiten wechseln in einen Dienst Proxy.</span><span class="sxs-lookup"><span data-stu-id="7ea61-147">These responsibilities move into a service proxy.</span></span> <span data-ttu-id="7ea61-148">Wird als bezeichnet `Sidecar pattern`, wird der Proxy in einem separaten Prozess bereitgestellt, um die Isolation von Ihrem Geschäfts Code bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="7ea61-148">Referred to as the `Sidecar pattern`, the proxy is deployed into a separate process to provide isolation from your business code.</span></span>

- <span data-ttu-id="7ea61-149">**Observability** ist ein wichtiger Entwurfs Aspekt bei der Cloud-native Anwendung.</span><span class="sxs-lookup"><span data-stu-id="7ea61-149">**Observability** is a key design consideration for cloud-native applications.</span></span> <span data-ttu-id="7ea61-150">Wenn Dienste auf einen Cluster von Knoten verteilt werden, wird die zentralisierte Protokollierung, Überwachung und Warnungen obligatorisch.</span><span class="sxs-lookup"><span data-stu-id="7ea61-150">As services are distributed across a cluster of nodes, centralized logging, monitoring, and alerts, become mandatory.</span></span> <span data-ttu-id="7ea61-151">Azure Monitor ist eine Sammlung von cloudbasierten Tools, die einen Einblick in den Zustand Ihres Systems bieten.</span><span class="sxs-lookup"><span data-stu-id="7ea61-151">Azure Monitor is a collection of cloud-based tools designed to provide visibility into the state of your system.</span></span>

- <span data-ttu-id="7ea61-152">**Infrastructure as Code** ist eine weit verbreitete Praxis, die die Platt Form Bereitstellung automatisiert.</span><span class="sxs-lookup"><span data-stu-id="7ea61-152">**Infrastructure as Code** is a widely accepted practice that automates platform provisioning.</span></span> <span data-ttu-id="7ea61-153">Ihre Infrastruktur und bereit Stellungen sind automatisiert, konsistent und wiederholbar.</span><span class="sxs-lookup"><span data-stu-id="7ea61-153">Your infrastructure and deployments are automated, consistent, and repeatable.</span></span> <span data-ttu-id="7ea61-154">Tools wie Azure Resource Manager, TERRAFORM und die Azure CLI ermöglichen es Ihnen, deklarativ Skripts für die erforderliche cloudinfrastruktur zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7ea61-154">Tools like Azure Resource Manager, Terraform, and the Azure CLI, enable you to declaratively script the cloud infrastructure you require.</span></span>

- <span data-ttu-id="7ea61-155">Die **Code Automatisierung** ist eine Voraussetzung für Native Cloud-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="7ea61-155">**Code automation** is a requirement for cloud-native applications.</span></span> <span data-ttu-id="7ea61-156">Moderne CI/CD-Systeme helfen dabei, dieses Prinzip zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="7ea61-156">Modern CI/CD systems help fulfill this principle.</span></span> <span data-ttu-id="7ea61-157">Sie bieten separate Build-und Bereitstellungs Schritte, die den konsistenten und qualitativ hochwertigen Code sicherstellen.</span><span class="sxs-lookup"><span data-stu-id="7ea61-157">They provide separate build and deployment steps that help ensure consistent and quality code.</span></span> <span data-ttu-id="7ea61-158">Die Buildphase wandelt den Code in ein binäres artefaktelement um.</span><span class="sxs-lookup"><span data-stu-id="7ea61-158">The build stage transforms the code into a binary artifact.</span></span> <span data-ttu-id="7ea61-159">Die Releasephase übernimmt das binäre artefaktelement, wendet die Konfiguration der externen Umgebung an und stellt Sie in einer angegebenen Umgebung bereit.</span><span class="sxs-lookup"><span data-stu-id="7ea61-159">The release stage picks up the binary artifact, applies external environment configuration, and deploys it to a specified environment.</span></span> <span data-ttu-id="7ea61-160">Azure devops und GitHub sind voll funktionsfähigen devops-Umgebungen.</span><span class="sxs-lookup"><span data-stu-id="7ea61-160">Azure DevOps and GitHub are full-featured DevOps environments.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="7ea61-161">Vorherige</span><span class="sxs-lookup"><span data-stu-id="7ea61-161">Previous</span></span>](application-bundles.md)