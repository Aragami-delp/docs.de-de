---
title: Abrufen von Setupinformationen aus einer Anwendungsdomäne
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- AppDomainSetup object
- retrieving setup information
- application domains, retrieving setup information
ms.assetid: 5cdb12ae-1e37-4a62-8ec7-93d6dcc6e8d9
ms.openlocfilehash: 4d06a8a3ccfa35af283323478ee44a7da63d896d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119739"
---
# <a name="retrieving-setup-information-from-an-application-domain"></a><span data-ttu-id="f3cf0-102">Abrufen von Setupinformationen aus einer Anwendungsdomäne</span><span class="sxs-lookup"><span data-stu-id="f3cf0-102">Retrieving Setup Information from an Application Domain</span></span>
<span data-ttu-id="f3cf0-103">Jede Instanz einer Anwendungsdomäne besteht sowohl aus Eigenschaften als auch aus <xref:System.AppDomainSetup>-Informationen.</span><span class="sxs-lookup"><span data-stu-id="f3cf0-103">Each instance of an application domain consists of both properties and <xref:System.AppDomainSetup> information.</span></span> <span data-ttu-id="f3cf0-104">Sie können Setupinformationen aus einer Anwendungsdomäne mit der Klasse <xref:System.AppDomain?displayProperty=nameWithType> abrufen.</span><span class="sxs-lookup"><span data-stu-id="f3cf0-104">You can retrieve setup information from an application domain using the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="f3cf0-105">Diese Klasse stellt mehrere Member zur Verfügung, die Konfigurierungsinformationen zu Anwendungsdomänen abrufen.</span><span class="sxs-lookup"><span data-stu-id="f3cf0-105">This class provides several members that retrieve configuration information about an application domain.</span></span>  
  
 <span data-ttu-id="f3cf0-106">Sie können das Objekt **AppDomainSetup** für die Anwendungsdomäne abfragen, um Setupinformationen zu erhalten, die der Erstellung an die Domäne übergeben wurden.</span><span class="sxs-lookup"><span data-stu-id="f3cf0-106">You can also query the **AppDomainSetup** object for the application domain to obtain setup information that was passed to the domain when it was created.</span></span>  
  
 <span data-ttu-id="f3cf0-107">Im folgenden Beispiel wird eine neue Anwendungsdomäne erstellt, und anschließend werden mehrere Memberwerte an die Konsole ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="f3cf0-107">The following example creates a new application domain and then prints several member values to the console.</span></span>  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 <span data-ttu-id="f3cf0-108">In folgendem Beispielen werden Setupinformationen für die Anwendungsdomäne festgelegt und anschließend abgerufen.</span><span class="sxs-lookup"><span data-stu-id="f3cf0-108">The following example sets, and then retrieves, setup information for an application domain.</span></span> <span data-ttu-id="f3cf0-109">Beachten Sie, dass `AppDomain.SetupInformation.ApplicationBase` die Konfigurationsinformationen abruft.</span><span class="sxs-lookup"><span data-stu-id="f3cf0-109">Note that `AppDomain.SetupInformation.ApplicationBase` gets the configuration information.</span></span>  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="f3cf0-110">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f3cf0-110">See also</span></span>

- [<span data-ttu-id="f3cf0-111">Programming with Application Domains (Programmieren mit Anwendungsdomänen)</span><span class="sxs-lookup"><span data-stu-id="f3cf0-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="f3cf0-112">Verwenden von Anwendungsdomänen</span><span class="sxs-lookup"><span data-stu-id="f3cf0-112">Using Application Domains</span></span>](use.md)
