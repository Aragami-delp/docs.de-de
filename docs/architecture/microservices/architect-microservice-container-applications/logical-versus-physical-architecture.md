---
title: Logische und physische Architektur im Vergleich
description: Unterschiede verstehen zwischen logischer und physischer Architektur
ms.date: 09/20/2018
ms.openlocfilehash: c269369e9b5391e8d25ece46e6b08e34a82fbbba
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2019
ms.locfileid: "68673057"
---
# <a name="logical-architecture-versus-physical-architecture"></a><span data-ttu-id="8e736-103">Logische und physische Architektur im Vergleich</span><span class="sxs-lookup"><span data-stu-id="8e736-103">Logical architecture versus physical architecture</span></span>

<span data-ttu-id="8e736-104">Zunächst einmal soll der Unterschied zwischen logischer und physischer Architektur beschrieben und erläutert werden, wie diese Architekturen auf das Design von auf einem Microservice basierenden Anwendungen anwendbar sind.</span><span class="sxs-lookup"><span data-stu-id="8e736-104">It's useful at this point to stop and discuss the distinction between logical architecture and physical architecture, and how this applies to the design of microservice-based applications.</span></span>

<span data-ttu-id="8e736-105">Für das Erstellen von Microservices sind keine spezifischen Technologien erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8e736-105">To begin, building microservices doesn't require the use of any specific technology.</span></span> <span data-ttu-id="8e736-106">Beispielsweise sind keine Docker-Container erforderlich, um eine auf einem Microservice basierende Architektur zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="8e736-106">For instance, Docker containers aren't mandatory to create a microservice-based architecture.</span></span> <span data-ttu-id="8e736-107">Diese Microservices könnten auch als einfache Prozesse ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="8e736-107">Those microservices could also be run as plain processes.</span></span> <span data-ttu-id="8e736-108">Microservices bauen auf einer logischen Architektur auf.</span><span class="sxs-lookup"><span data-stu-id="8e736-108">Microservices is a logical architecture.</span></span>

<span data-ttu-id="8e736-109">Zudem ist diese Parität eines Unternehmensmicroservice und physischem Dienst oder Container nicht immer erforderlich, wenn Sie eine umfangreiche und komplexe Anwendung erstellen, die aus dutzenden oder sogar hunderten von Diensten besteht. Dies ist auch nicht der Fall, wenn ein Microservice physisch als einzelner Dienst, Prozess oder Container implementiert werden könnte (der Einfachheit halber wird dieser Ansatz in der ersten Version von [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) angewendet).</span><span class="sxs-lookup"><span data-stu-id="8e736-109">Moreover, even when a microservice could be physically implemented as a single service, process, or container (for simplicity's sake, that's the approach taken in the initial version of [eShopOnContainers](https://aka.ms/MicroservicesArchitecture)), this parity between business microservice and physical service or container isn't necessarily required in all cases when you build a large and complex application composed of many dozens or even hundreds of services.</span></span>

<span data-ttu-id="8e736-110">In diesem Zusammenhang besteht ein Unterschied zwischen der logischen und der physischen Architektur einer Anwendung.</span><span class="sxs-lookup"><span data-stu-id="8e736-110">This is where there's a difference between an application's logical architecture and physical architecture.</span></span> <span data-ttu-id="8e736-111">Die logische Architektur und die logischen Begrenzungen eines Systems können nicht in jeder einzelnen Komponente der physischen Architektur bzw. der Bereitstellungsarchitektur zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="8e736-111">The logical architecture and logical boundaries of a system do not necessarily map one-to-one to the physical or deployment architecture.</span></span> <span data-ttu-id="8e736-112">Dies ist zwar möglich, allerdings ist es nur selten der Fall.</span><span class="sxs-lookup"><span data-stu-id="8e736-112">It can happen, but it often doesn't.</span></span>

<span data-ttu-id="8e736-113">Auch wenn Sie möglicherweise einen bestimmten Unternehmensmicroservice oder einen begrenzten Kontext ermittelt haben, bedeutet dies nicht, dass die Erstellung eines einzelnen Diensts (z.B. eine ASP.NET-Web-API) oder eines einzelnen Docker-Containers für jeden Unternehmensmicroservice immer die beste Möglichkeit darstellt, diese zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="8e736-113">Although you might have identified certain business microservices or Bounded Contexts, it doesn't mean that the best way to implement them is always by creating a single service (such as an ASP.NET Web API) or single Docker container for each business microservice.</span></span> <span data-ttu-id="8e736-114">Wenn Sie über eine Regel verfügen, die festlegt, dass jeder Unternehmensmicroservice über einen einzelnen Dienst oder Container implementiert werden muss, schränkt Sie das zu sehr ein.</span><span class="sxs-lookup"><span data-stu-id="8e736-114">Having a rule saying each business microservice has to be implemented using a single service or container is too rigid.</span></span>

<span data-ttu-id="8e736-115">Aus diesem Grund handelt es sich bei einem Unternehmensmicroservice oder bei einem begrenzten Kontext um eine logische Architektur, die sich möglicherweise mit der physischen Architektur überschneidet.</span><span class="sxs-lookup"><span data-stu-id="8e736-115">Therefore, a business microservice or Bounded Context is a logical architecture that might coincide (or not) with physical architecture.</span></span> <span data-ttu-id="8e736-116">Wichtig ist, dass der Unternehmensmicroservice oder der begrenzte Kontext autonom sind. Dies erreichen Sie, indem Sie zulassen, dass für Codes und Zustand unabhängige Versionen erstellt und diese unabhängig bereitgestellt und skaliert werden.</span><span class="sxs-lookup"><span data-stu-id="8e736-116">The important point is that a business microservice or Bounded Context must be autonomous by allowing code and state to be independently versioned, deployed, and scaled.</span></span>

<span data-ttu-id="8e736-117">Wie in der Abbildung 4-8 dargestellt, kann der Katalogunternehmensmicroservice ggf. aus mehreren Diensten oder Prozessen bestehen.</span><span class="sxs-lookup"><span data-stu-id="8e736-117">As Figure 4-8 shows, the catalog business microservice could be composed of several services or processes.</span></span> <span data-ttu-id="8e736-118">Dabei kann es sich um mehrere ASP.NET-Web-API-Dienste oder um beliebige Dienste handeln, die HTTP oder ein beliebiges anderes Protokoll verwenden.</span><span class="sxs-lookup"><span data-stu-id="8e736-118">These could be multiple ASP.NET Web API services or any other kind of services using HTTP or any other protocol.</span></span> <span data-ttu-id="8e736-119">Vor allem können die Dienste ggf. alle auf dieselben Daten zugreifen, solange sie sich eine Geschäftsdomäne teilen.</span><span class="sxs-lookup"><span data-stu-id="8e736-119">More importantly, the services could share the same data, as long as these services are cohesive with respect to the same business domain.</span></span>

![Diagramm des Katalogunternehmensmicroservice, der einen API-Dienst, einen Suchdienst und eine SQL Server-Datenbank enthält.](./media/image8.png)

<span data-ttu-id="8e736-121">**Abbildung 4-8**.</span><span class="sxs-lookup"><span data-stu-id="8e736-121">**Figure 4-8**.</span></span> <span data-ttu-id="8e736-122">Unternehmensmicroservice mit mehreren physischen Diensten</span><span class="sxs-lookup"><span data-stu-id="8e736-122">Business microservice with several physical services</span></span>

<span data-ttu-id="8e736-123">Die Dienste in diesem Beispiel verfügen alle über dasselbe Datenmodell, da der Web-API-Dienst auf dieselben Daten ausgerichtet ist wie der Suchdienst.</span><span class="sxs-lookup"><span data-stu-id="8e736-123">The services in the example share the same data model because the Web API service targets the same data as the Search service.</span></span> <span data-ttu-id="8e736-124">D.h., Sie teilen diese Funktion für die physische Implementierung des Unternehmensmicroservices auf, damit Sie diese internen Dienste nach Belieben zentral hoch- oder herunterskalieren können.</span><span class="sxs-lookup"><span data-stu-id="8e736-124">So, in the physical implementation of the business microservice, you're splitting that functionality so you can scale each of those internal services up or down as needed.</span></span> <span data-ttu-id="8e736-125">Es kann sein, dass der Web-API-Dienst mehr Instanzen benötigt als der Suchdienst – oder umgekehrt.</span><span class="sxs-lookup"><span data-stu-id="8e736-125">Maybe the Web API service usually needs more instances than the Search service, or vice versa.</span></span>

<span data-ttu-id="8e736-126">Zusammenfassend lässt sich sagen, dass sich die logische Architektur von Microservices nicht immer mit der physischen Bereitstellungsarchitektur überschneiden muss.</span><span class="sxs-lookup"><span data-stu-id="8e736-126">In short, the logical architecture of microservices doesn't always have to coincide with the physical deployment architecture.</span></span> <span data-ttu-id="8e736-127">In diesem Handbuch ist mit dem Begriff „Microservice“ immer ein logischer Microservice oder ein Unternehmensmicroservice gemeint, der mindestens einem (physischen) Dienst zugeordnet werden kann.</span><span class="sxs-lookup"><span data-stu-id="8e736-127">In this guide, whenever we mention a microservice, we mean a business or logical microservice that could map to one or more (physical) services.</span></span> <span data-ttu-id="8e736-128">In den meisten Fällen handelt es sich nur um einen einzelnen Dienst. Es können aber auch mehr Dienste zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="8e736-128">In most cases, this will be a single service, but it might be more.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8e736-129">[Zurück](data-sovereignty-per-microservice.md)
>[Weiter](distributed-data-management.md)</span><span class="sxs-lookup"><span data-stu-id="8e736-129">[Previous](data-sovereignty-per-microservice.md)
[Next](distributed-data-management.md)</span></span>