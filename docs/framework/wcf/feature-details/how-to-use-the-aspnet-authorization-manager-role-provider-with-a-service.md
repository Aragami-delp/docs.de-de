---
title: 'Vorgehensweise: Verwenden des Rollenanbieters für den ASP.NET-Autorisierungs-Manager bei einem Dienst'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 7c1076671512b33f115950cad684fba0b514abe9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595335"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="630e6-102">Vorgehensweise: Verwenden des Rollenanbieters für den ASP.NET-Autorisierungs-Manager bei einem Dienst</span><span class="sxs-lookup"><span data-stu-id="630e6-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>
<span data-ttu-id="630e6-103">Wenn ASP.net einen Webdienst hostet, können Sie den Autorisierungs-Manager in die Anwendung integrieren, um die Autorisierung für den Dienst bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="630e6-103">When ASP.NET hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="630e6-104">Der Autorisierungs-Manager ermöglicht einem Anwendungsentwickler das Definieren einzelner Vorgänge, die zum Bilden von Aufgaben zusammengruppiert werden können.</span><span class="sxs-lookup"><span data-stu-id="630e6-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="630e6-105">Ein Administrator kann anschließend Rollen für das Ausführen bestimmter Aufgaben oder einzelner Vorgänge autorisieren.</span><span class="sxs-lookup"><span data-stu-id="630e6-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="630e6-106">Vom Autorisierungs-Manager wird ein Verwaltungstool als Microsoft Management Console (MMC)-Snap-in für die Verwaltung von Rollen, Aufgaben, Vorgängen und Benutzern zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="630e6-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="630e6-107">Administratoren konfigurieren für den Autorisierungs-Manager einen Richtlinienspeicher in einer XML-Datei, in Active Directory oder in einem ADAM (Active Directory Application Mode)-Speicher.</span><span class="sxs-lookup"><span data-stu-id="630e6-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="630e6-108">Der Autorisierungs-Manager wird in die Anwendung integriert, indem der Autorisierungs-Manager ASP.NET-Rollen Anbieter für die ASP.NET-Anwendung konfiguriert wird, die den Webdienst gehostet.</span><span class="sxs-lookup"><span data-stu-id="630e6-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager ASP.NET role provider for the ASP.NET application that is hosting the Web service.</span></span> <span data-ttu-id="630e6-109">Wie andere ASP.NET-Rollen Anbieter wird der Autorisierungs-Manager ASP.NET-Rollen Anbieter mithilfe des <`providers`>-Elements konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="630e6-109">Like other ASP.NET role providers, the Authorization Manager ASP.NET role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="630e6-110">Das folgende Codebeispiel ist ein Teil einer Konfigurationsdatei für einen Webdienst, der den Autorisierungs-Manager in die Anwendung integriert.</span><span class="sxs-lookup"><span data-stu-id="630e6-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
```xml  
<system.web>  
    <roleManager enabled="true" defaultProvider="AzManRoleProvider">  
      <providers>  
        <add name="AzManRoleProvider"  
             type="System.Web.Security.AuthorizationStoreRoleProvider, System.Web, Version=2.0.0.0, Culture=neutral, publicKeyToken=b03f5f7f11d50a3a"  
             connectionStringName="AzManPolicyStoreConnectionString"
             applicationName="SecureService"/>  
      </providers>  
    </roleManager>  
</system.web>  
```  
  
 <span data-ttu-id="630e6-111">Weitere Informationen zum Integrieren eines ASP.NET-Rollen Anbieters in eine WCF-Anwendung finden [Sie unter Gewusst wie: Verwenden des ASP.NET-Rollen Anbieters mit einem-Dienst](how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="630e6-111">For more information about integrating an ASP.NET role provider with a WCF application, see [How to: Use the ASP.NET Role Provider with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> <span data-ttu-id="630e6-112">Weitere Informationen zur Verwendung des Autorisierungs-Managers mit ASP.net finden Sie unter Gewusst [wie: Verwenden des Autorisierungs-Managers (AzMan) mit ASP.NET 2,0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="630e6-112">For more information about using Authorization Manager with ASP.NET, see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="630e6-113">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="630e6-113">See also</span></span>

- [<span data-ttu-id="630e6-114">Vorgehensweise: Verwenden des Rollenanbieters für den ASP.NET bei einem Dienst</span><span class="sxs-lookup"><span data-stu-id="630e6-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)
