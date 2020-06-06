---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 598b341e8b09acd11ba215e6add3adf9e44b2b81
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400466"
---
# \<custom>
<span data-ttu-id="118a5-101">Gibt die spezifischen Einstellungen für einen benutzerdefinierten Peerresolverdienst an.</span><span class="sxs-lookup"><span data-stu-id="118a5-101">Specifies settings for a custom peer resolver service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<resolver>**](resolver.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<custom>**  
  
## <a name="syntax"></a><span data-ttu-id="118a5-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="118a5-102">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="118a5-103">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="118a5-103">Attributes and Elements</span></span>  
 <span data-ttu-id="118a5-104">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="118a5-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="118a5-105">Attribute</span><span class="sxs-lookup"><span data-stu-id="118a5-105">Attributes</span></span>  
  
|<span data-ttu-id="118a5-106">attribute</span><span class="sxs-lookup"><span data-stu-id="118a5-106">Attribute</span></span>|<span data-ttu-id="118a5-107">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="118a5-107">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="118a5-108">Ein URI, der die Endpunktadresse des Peerknotens angibt, der den benutzerdefinierten Peerresolverdienst hostet.</span><span class="sxs-lookup"><span data-stu-id="118a5-108">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="118a5-109">Eine Zeichenfolge, die den Typ des benutzerdefinierten Peerresolverdiensts angibt.</span><span class="sxs-lookup"><span data-stu-id="118a5-109">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="118a5-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="118a5-110">Child Elements</span></span>  
  
|<span data-ttu-id="118a5-111">Element</span><span class="sxs-lookup"><span data-stu-id="118a5-111">Element</span></span>|<span data-ttu-id="118a5-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="118a5-112">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="118a5-113">Gibt die Identität für benutzerdefinierte Peerresolver an, die mit diesem Element konfiguriert wurden.</span><span class="sxs-lookup"><span data-stu-id="118a5-113">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="118a5-114">Dieses Element ist vom Typ <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="118a5-114">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[\<headers>](headers-element.md)|<span data-ttu-id="118a5-115">Eine Auflistung von Adressheadern, die für SOAP-Nachrichten verwendet werden, die vom benutzerdefinierten Peerresolver verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="118a5-115">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="118a5-116">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="118a5-116">Parent Elements</span></span>  
  
|<span data-ttu-id="118a5-117">Element</span><span class="sxs-lookup"><span data-stu-id="118a5-117">Element</span></span>|<span data-ttu-id="118a5-118">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="118a5-118">Description</span></span>|  
|-------------|-----------------|  
|[\<resolver>](resolver.md)|<span data-ttu-id="118a5-119">Ein Peerresolver, der zum Auflösen einer Peermesh-ID in einen Satz von Peerknotenadressen verwendet wird, der mehrere Knoten im Mesh darstellt.</span><span class="sxs-lookup"><span data-stu-id="118a5-119">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="118a5-120">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="118a5-120">Remarks</span></span>  
 <span data-ttu-id="118a5-121">Mit diesem Element werden die Basiseinstellungen für einen benutzerdefinierten Peerresolverdienst definiert. Berücksichtigt werden dabei unter anderem die Endpunktadresse des Peers, der den Dienst hostet, sowie alle spezifischen Bindungseinstellungen.</span><span class="sxs-lookup"><span data-stu-id="118a5-121">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="118a5-122">Weitere Informationen zum Erstellen eines benutzerdefinierten Konflikt Lösers finden [Sie unter Hinzufügen eines benutzerdefinierten Resolvers zu einer PeerChannel-Anwendung](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="118a5-122">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="118a5-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="118a5-123">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="118a5-124">Peerresolver</span><span class="sxs-lookup"><span data-stu-id="118a5-124">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="118a5-125">[Hinzufügen einer benutzerdefinierten Auflösung zu einer PeerChannel-Anwendung](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="118a5-125">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
