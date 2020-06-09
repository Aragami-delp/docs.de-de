---
title: Migrieren von .NET-Remoteanwendungen nach WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: d12583904e4a025a8de1103f0fb48f4656d6855e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598774"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="b6c39-102">Migrieren von .NET-Remoteanwendungen nach WCF</span><span class="sxs-lookup"><span data-stu-id="b6c39-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="b6c39-103">**Dieses Thema ist spezifisch für eine Legacy Technologie, die aus Gründen der Abwärtskompatibilität mit vorhandenen Anwendungen beibehalten wird und nicht für die neue Entwicklung empfohlen wird. Verteilte Anwendungen sollten jetzt mithilfe von WCF entwickelt werden.**</span><span class="sxs-lookup"><span data-stu-id="b6c39-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using WCF.**</span></span>  
  
 <span data-ttu-id="b6c39-104">Es gibt zwei Möglichkeiten, WCF mit vorhandenen .NET Remoting-Anwendungen zu nutzen: Integration und Migration.</span><span class="sxs-lookup"><span data-stu-id="b6c39-104">There are two ways to take advantage of WCF with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="b6c39-105">Integration ermöglicht es Ihnen, .NET Remoting 2,0 und WCF nebeneinander auszuführen, sodass Sie dieselben Geschäftsobjekte über beide Technologien gleichzeitig verfügbar machen können, ohne Ihren vorhandenen .NET Remoting 2,0-Code ändern zu müssen.</span><span class="sxs-lookup"><span data-stu-id="b6c39-105">Integration allows you to have .NET Remoting 2.0 and WCF running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .NET Remoting 2.0 code.</span></span> <span data-ttu-id="b6c39-106">Für die Integration ist es erforderlich, dass Sie auf .NET Framework 2,0 oder höher ausführen.</span><span class="sxs-lookup"><span data-stu-id="b6c39-106">Integration requires that you are running on .NET Framework 2.0 or greater.</span></span> <span data-ttu-id="b6c39-107">Wenn Sie WCF-Features nutzen und keine Netzwerkkompatibilität mit Remoting 2,0-Systemen benötigen, können Sie den gesamten Dienst zu WCF migrieren.</span><span class="sxs-lookup"><span data-stu-id="b6c39-107">If you want to take advantage of WCF features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to WCF.</span></span> <span data-ttu-id="b6c39-108">Für die Migration von .NET Remoting 2,0 zu WCF sind Änderungen an der Schnittstelle des Remote Objekts und seinen Konfigurationseinstellungen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b6c39-108">Migration from .NET Remoting 2.0 to WCF requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="b6c39-109">Beide Themen werden unter [Remoting zum Windows Communication Foundation](https://docs.microsoft.com/previous-versions/aa730857(v=vs.80))behandelt.</span><span class="sxs-lookup"><span data-stu-id="b6c39-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](https://docs.microsoft.com/previous-versions/aa730857(v=vs.80)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6c39-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b6c39-110">See also</span></span>

- [<span data-ttu-id="b6c39-111">Konzeptionelle Übersicht</span><span class="sxs-lookup"><span data-stu-id="b6c39-111">Conceptual Overview</span></span>](../conceptual-overview.md)
