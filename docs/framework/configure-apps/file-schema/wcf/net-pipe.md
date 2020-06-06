---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: dd984b2ab89060451b1b2d02c324e803766908ce
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397715"
---
# \<net.pipe>
<span data-ttu-id="7f4d0-102">Gibt Konfigurationseinstellungen für den Aktivierungsdienst der benannten Pipes an, der die Lebensdauer der Verbindung der benannten Pipes verwaltet und Aktivierungsanforderungen verarbeitet, die über benannte Pipes eintreffen.</span><span class="sxs-lookup"><span data-stu-id="7f4d0-102">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.pipe>**  
  
## <a name="syntax"></a><span data-ttu-id="7f4d0-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="7f4d0-103">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.pipe maxPendingAccepts="Integer"
              maxPendingConnections="Integer"
              receiveTimeout="TimeSpan">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="7f4d0-104">type</span><span class="sxs-lookup"><span data-stu-id="7f4d0-104">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f4d0-105">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="7f4d0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7f4d0-106">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="7f4d0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f4d0-107">Attribute</span><span class="sxs-lookup"><span data-stu-id="7f4d0-107">Attributes</span></span>  
  
|<span data-ttu-id="7f4d0-108">attribute</span><span class="sxs-lookup"><span data-stu-id="7f4d0-108">Attribute</span></span>|<span data-ttu-id="7f4d0-109">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="7f4d0-109">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="7f4d0-110">Eine ganze Zahl, die den Höchstwert für ausstehende gleichzeitig annehmende Threads am überwachenden Endpunkt für den Freigabedienst festlegt.</span><span class="sxs-lookup"><span data-stu-id="7f4d0-110">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="7f4d0-111">Der Standardwert ist 2.</span><span class="sxs-lookup"><span data-stu-id="7f4d0-111">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="7f4d0-112">Eine ganze Zahl, die die maximale Anzahl von Verbindungen angibt, die auf eine Verteilung warten können.</span><span class="sxs-lookup"><span data-stu-id="7f4d0-112">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="7f4d0-113">Der Standardwert ist 100.</span><span class="sxs-lookup"><span data-stu-id="7f4d0-113">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="7f4d0-114">Eine <xref:System.TimeSpan>, die das Timeout für das Lesen der Rahmendaten und das Ausführen der Verbindungsverteilung der zugrunde liegenden Verbindungen angibt.</span><span class="sxs-lookup"><span data-stu-id="7f4d0-114">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="7f4d0-115">Der Standardwert ist "00:00:10".</span><span class="sxs-lookup"><span data-stu-id="7f4d0-115">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f4d0-116">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7f4d0-116">Child Elements</span></span>  
  
|<span data-ttu-id="7f4d0-117">Element</span><span class="sxs-lookup"><span data-stu-id="7f4d0-117">Element</span></span>|<span data-ttu-id="7f4d0-118">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7f4d0-118">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="7f4d0-119">Eine Auflistung von Konfigurationselementen, die ein `securityIdentifier` -Attribut zum Angeben von Benutzerkonten für Prozesse enthalten, die WCF-Dienste hosten und Verbindungs Zugriff auf den Freigabe Dienst erhalten.</span><span class="sxs-lookup"><span data-stu-id="7f4d0-119">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f4d0-120">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7f4d0-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7f4d0-121">Element</span><span class="sxs-lookup"><span data-stu-id="7f4d0-121">Element</span></span>|<span data-ttu-id="7f4d0-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7f4d0-122">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="7f4d0-123">Enthält Konfigurationseinstellungen für den Listenerprozess SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="7f4d0-123">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f4d0-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7f4d0-124">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
