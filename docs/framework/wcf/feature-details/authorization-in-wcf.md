---
title: Autorisierung in WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: d67d64dcf0003de28775ac947f8b5f72d7c2ba2a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597630"
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="2c3c7-102">Autorisierung in WCF</span><span class="sxs-lookup"><span data-stu-id="2c3c7-102">Authorization in WCF</span></span>
<span data-ttu-id="2c3c7-103">Autorisierung ist der Prozess, Zugriff und Rechte für Ressourcen zu steuern, z. B. Dienste oder Dateien.</span><span class="sxs-lookup"><span data-stu-id="2c3c7-103">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="2c3c7-104">In den Themen in diesem Abschnitt wird erläutert, wie Sie diese grundlegende Aufgabe in Windows Communication Foundation (WCF) auf unterschiedlichste Weise ausführen.</span><span class="sxs-lookup"><span data-stu-id="2c3c7-104">The topics in this section show you how to perform this basic task in Windows Communication Foundation (WCF) in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2c3c7-105">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="2c3c7-105">In This Section</span></span>  
 [<span data-ttu-id="2c3c7-106">Zugriffssteuerungsmechanismen</span><span class="sxs-lookup"><span data-stu-id="2c3c7-106">Access Control Mechanisms</span></span>](access-control-mechanisms.md)  
 <span data-ttu-id="2c3c7-107">Bietet eine kurze Übersicht über die Autorisierungs Mechanismen in WCF und empfohlene Verwendungsmöglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="2c3c7-107">Provides a brief outline of the authorization mechanisms in WCF, and suggested uses.</span></span>  
  
 [<span data-ttu-id="2c3c7-108">Vorgehensweise: Einschränken des Zugriffs mit der PrincipalPermissionAttribute-Klasse</span><span class="sxs-lookup"><span data-stu-id="2c3c7-108">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="2c3c7-109">Zeigt den Prozess zum Zugriff auf einen Dienst mit dem <xref:System.Security.Permissions.PrincipalPermissionAttribute> an.</span><span class="sxs-lookup"><span data-stu-id="2c3c7-109">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="2c3c7-110">Vorgehensweise: Verwenden des Rollenanbieters für den ASP.NET bei einem Dienst</span><span class="sxs-lookup"><span data-stu-id="2c3c7-110">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="2c3c7-111">Führt Sie durch die Konfiguration eines Dienstanbieters, um die Verwendung der Rollen Anbieter Funktion von ASP.net zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="2c3c7-111">Walks through the configuration of a service to enable it to use the role provider feature of ASP.NET.</span></span>  
  
 [<span data-ttu-id="2c3c7-112">Vorgehensweise: Verwenden des Rollenanbieters für den ASP.NET-Autorisierungs-Manager bei einem Dienst</span><span class="sxs-lookup"><span data-stu-id="2c3c7-112">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 <span data-ttu-id="2c3c7-113">ASP.net kann den Autorisierungs-Manager verwenden, um die Autorisierung für eine Website zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="2c3c7-113">ASP.NET can use the Authorization Manager to manage authorization for a Web site.</span></span> <span data-ttu-id="2c3c7-114">WCF kann die Kombination von ASP.net/Authorization Manager auch für die Autorisierung von Clients nutzen.</span><span class="sxs-lookup"><span data-stu-id="2c3c7-114">WCF can similarly leverage the ASP.NET/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="2c3c7-115">Verwalten von Ansprüchen und Autorisierung mit dem Identitätsmodell</span><span class="sxs-lookup"><span data-stu-id="2c3c7-115">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="2c3c7-116">Erläutert die Grundlagen des Verwendens der Identitätsmodellinfrastruktur für auf Ansprüche basierende Autorisierung.</span><span class="sxs-lookup"><span data-stu-id="2c3c7-116">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="2c3c7-117">Delegierung und Identitätswechsel</span><span class="sxs-lookup"><span data-stu-id="2c3c7-117">Delegation and Impersonation</span></span>](delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="2c3c7-118">Erläutert den Unterschied zwischen Delegierung und Identitätswechsel.</span><span class="sxs-lookup"><span data-stu-id="2c3c7-118">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2c3c7-119">Referenz</span><span class="sxs-lookup"><span data-stu-id="2c3c7-119">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="2c3c7-120">Verwandte Abschnitte</span><span class="sxs-lookup"><span data-stu-id="2c3c7-120">Related Sections</span></span>  
 [<span data-ttu-id="2c3c7-121">Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="2c3c7-121">Authentication</span></span>](authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="2c3c7-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2c3c7-122">See also</span></span>

- [<span data-ttu-id="2c3c7-123">Sicherheitsübersicht</span><span class="sxs-lookup"><span data-stu-id="2c3c7-123">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="2c3c7-124">[Sicherheitsmodell für Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="2c3c7-124">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
