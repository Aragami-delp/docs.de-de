---
title: Überwachen von Containeranwendungsdiensten
description: Lernen Sie einige wichtige Aspekte des Überwachens von Containerarchitekturen kennen.
ms.date: 02/15/2019
ms.openlocfilehash: e41df53ad94784436442c3cf7defed3fab510455
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374441"
---
# <a name="monitor-containerized-application-services"></a><span data-ttu-id="41801-103">Überwachen von Containeranwendungsdiensten</span><span class="sxs-lookup"><span data-stu-id="41801-103">Monitor containerized application services</span></span>

<span data-ttu-id="41801-104">Für Anwendungen, die in mehrere Container und Microservices aufgeteilt sind, ist die Verfügbarkeit eines Verfahrens zum Überprüfen und Analysieren des Verhaltens der gesamten Anwendung kritisch.</span><span class="sxs-lookup"><span data-stu-id="41801-104">It's critical for applications split into multiple containers and microservices to have a way to monitor and analyze the behavior of the whole application.</span></span>

## <a name="azure-monitor"></a><span data-ttu-id="41801-105">Azure Monitor</span><span class="sxs-lookup"><span data-stu-id="41801-105">Azure Monitor</span></span>

<span data-ttu-id="41801-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) ist ein erweiterbarer Analysedienst, der Ihre Live-Anwendungen überwacht.</span><span class="sxs-lookup"><span data-stu-id="41801-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) is an extensible analytics service that monitors your live application.</span></span> <span data-ttu-id="41801-107">Er hilft Ihnen, Leistungsprobleme zu erkennen und zu diagnostizieren, und Sie können nachvollziehen, wie die Benutzer Ihre App nutzen.</span><span class="sxs-lookup"><span data-stu-id="41801-107">It helps you to detect and diagnose performance issues and to understand what users actually do with your app.</span></span> <span data-ttu-id="41801-108">Er wurde für Entwickler entworfen, in der Absicht, Sie bei der fortlaufenden Verbesserung von Leistung und Nutzbarkeit Ihrer Dienste oder Anwendungen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="41801-108">It's designed for developers, with the intent of helping you to continuously improve the performance and usability of your services or applications.</span></span> <span data-ttu-id="41801-109">Azure Monitor funktioniert sowohl mit Web/Diensten als auch mit eigenständigen Apps auf einer großen Bandbreite von Plattformen, wie .NET, Java, Node.js und vielen anderen, die lokal oder in der Cloud gehostet sein können.</span><span class="sxs-lookup"><span data-stu-id="41801-109">Azure Monitor works with both web/services and standalone apps on a wide variety of platforms like .NET, Java, Node.js and many other platforms, hosted on-premises or in the cloud.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="41801-110">Zusätzliche Ressourcen</span><span class="sxs-lookup"><span data-stu-id="41801-110">Additional resources</span></span>

- <span data-ttu-id="41801-111">**Übersicht über Azure Monitor** </span><span class="sxs-lookup"><span data-stu-id="41801-111">**Overview of Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="41801-112">**Was ist Application Insights?**</span><span class="sxs-lookup"><span data-stu-id="41801-112">**What is Application Insights?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="41801-113">**Was sind Azure Monitor-Metriken?**</span><span class="sxs-lookup"><span data-stu-id="41801-113">**What is Azure Monitor Metrics?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- <span data-ttu-id="41801-114">**Containerüberwachungslösung in Azure Monitor** </span><span class="sxs-lookup"><span data-stu-id="41801-114">**Container Monitoring solution in Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a><span data-ttu-id="41801-115">Sicherheits-und Sicherungsdienste</span><span class="sxs-lookup"><span data-stu-id="41801-115">Security and backup services</span></span>

<span data-ttu-id="41801-116">Es gibt eine Vielzahl von unterstützenden Pflichtarbeiten mit vielen Details, mit denen Sie sich abgeben müssen, um sicherzustellen, dass Ihre Anwendungen und Infrastruktur in erstklassigem Zustand sind, um Geschäftsanforderungen zu unterstützen, und die Situation wird im Bereich der Microservices noch komplizierter – daher brauchen Sie eine Möglichkeit, sowohl allgemeine als auch Detailansichten zur Hand zu haben, wenn Sie Aktionen einleiten müssen.</span><span class="sxs-lookup"><span data-stu-id="41801-116">There are many support chores with lots of details that you have to handle to ensure your applications and infrastructure are in top notch condition to support business needs, and the situation becomes more complicated in the microservices realm, so you need a way to have both high-level and detailed views when you need to take action.</span></span>

<span data-ttu-id="41801-117">Azure bietet die Tools, um vier kritische Aspekte Ihrer Cloud- und lokalen Ressourcen zu verwalten und einen einheitlichen Blick zu ermöglichen:</span><span class="sxs-lookup"><span data-stu-id="41801-117">Azure has the tools to manage and provide a unified view of four critical aspects of both your cloud and on-premises resources:</span></span>

- <span data-ttu-id="41801-118">**Sicherheit**.</span><span class="sxs-lookup"><span data-stu-id="41801-118">**Security**.</span></span> <span data-ttu-id="41801-119">Mit dem [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span><span class="sxs-lookup"><span data-stu-id="41801-119">With [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span></span>
  - <span data-ttu-id="41801-120">Erhalten Sie umfassende Transparenz und Kontrolle über die Sicherheit Ihrer virtuellen Computer, Apps und Workloads.</span><span class="sxs-lookup"><span data-stu-id="41801-120">Get full visibility and control over the security of your virtual machines, apps, and workloads.</span></span>
  - <span data-ttu-id="41801-121">Zentralisieren Sie die Verwaltung Ihrer Sicherheitsrichtlinien, und integrieren Sie vorhandene Prozesse und Tools.</span><span class="sxs-lookup"><span data-stu-id="41801-121">Centralize the management of your security policies and integrate existing processes and tools.</span></span>
  - <span data-ttu-id="41801-122">Erkennen Sie reale Bedrohungen mit erweiterter Analyse.</span><span class="sxs-lookup"><span data-stu-id="41801-122">Detect real threats with advanced analytics.</span></span>

- <span data-ttu-id="41801-123">**Sicherung**.</span><span class="sxs-lookup"><span data-stu-id="41801-123">**Backup**.</span></span> <span data-ttu-id="41801-124">Mit [Azure Backup](https://azure.microsoft.com/services/backup/).</span><span class="sxs-lookup"><span data-stu-id="41801-124">With [Azure Backup](https://azure.microsoft.com/services/backup/).</span></span>
  - <span data-ttu-id="41801-125">Vermeiden Sie kostspielige Unterbrechungen des Geschäfts, halten Sie Complianceziele ein, und schützen Sie Ihre Daten vor Ransomware und menschlichen Fehlern.</span><span class="sxs-lookup"><span data-stu-id="41801-125">Avoid costly business disruptions, meet compliance goals, and protect your data against ransomware and human errors.</span></span>
  - <span data-ttu-id="41801-126">Halten Sie Ihre Sicherungsdaten während der Übertragung und im Ruhezustand verschlüsselt.</span><span class="sxs-lookup"><span data-stu-id="41801-126">Keep your backup data encrypted in transit and at rest.</span></span>
  - <span data-ttu-id="41801-127">Stellen Sie Zugriff auf der Grundlage von mehrstufiger Authentifizierung sicher, um unberechtigte Nutzung zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="41801-127">Ensure access based on multifactor authentication to prevent unauthorized use.</span></span>

- <span data-ttu-id="41801-128">**Lokale Ressourcen**.</span><span class="sxs-lookup"><span data-stu-id="41801-128">**On-premises resources**.</span></span> <span data-ttu-id="41801-129">Mit [Hybrid-Cloud-Lösungen](https://azure.microsoft.com/solutions/hybrid-cloud-app/)</span><span class="sxs-lookup"><span data-stu-id="41801-129">With [hybrid cloud solutions](https://azure.microsoft.com/solutions/hybrid-cloud-app/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="41801-130">[Zurück](manage-production-docker-environments.md)
>[Weiter](../key-takeaways/index.md)</span><span class="sxs-lookup"><span data-stu-id="41801-130">[Previous](manage-production-docker-environments.md)
[Next](../key-takeaways/index.md)</span></span>
