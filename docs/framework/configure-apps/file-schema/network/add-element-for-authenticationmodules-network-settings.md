---
title: <add>-Element für authenticationModules (Netzwerkeinstellungen)
description: Das <add> Network settings-Element für connectionManagement fügt der Verbindungs Verwaltungsliste im .NET Framework eine IP-Adresse oder einen DNS-Namen hinzu.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/add
helpviewer_keywords:
- authenticationModules, add element
- add element, authenticationModules
- <authenticationModules>, add element
- <add> element, authenticationModules
ms.assetid: 333c5fb0-a2ab-4db8-8531-a7fe37bb9b5b
ms.openlocfilehash: 1a6d0f79f076a69cec33ac14f0e0f33f7c3c6577
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504640"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="010c9-103">\<add>-Element für authenticationModules (Netzwerkeinstellungen)</span><span class="sxs-lookup"><span data-stu-id="010c9-103">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="010c9-104">Fügt der Anwendung ein Authentifizierungs Modul hinzu.</span><span class="sxs-lookup"><span data-stu-id="010c9-104">Adds an authentication module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="010c9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="010c9-105">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="010c9-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="010c9-106">Attributes and Elements</span></span>  
 <span data-ttu-id="010c9-107">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="010c9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="010c9-108">Attribute</span><span class="sxs-lookup"><span data-stu-id="010c9-108">Attributes</span></span>  
  
|<span data-ttu-id="010c9-109">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="010c9-109">**Attribute**</span></span>|<span data-ttu-id="010c9-110">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="010c9-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="010c9-111">Der voll qualifizierte Typname (angegeben durch die <xref:System.Type.FullName%2A> -Eigenschaft) und der AssemblyName (angegeben durch die- <xref:System.Reflection.Assembly.FullName%2A> Eigenschaft), getrennt durch ein Komma.</span><span class="sxs-lookup"><span data-stu-id="010c9-111">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="010c9-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="010c9-112">Child Elements</span></span>  
 <span data-ttu-id="010c9-113">Keine</span><span class="sxs-lookup"><span data-stu-id="010c9-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="010c9-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="010c9-114">Parent Elements</span></span>  
  
|<span data-ttu-id="010c9-115">**Element**</span><span class="sxs-lookup"><span data-stu-id="010c9-115">**Element**</span></span>|<span data-ttu-id="010c9-116">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="010c9-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="010c9-117">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="010c9-117">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="010c9-118">Gibt Module an, die zum Authentifizieren von Netzwerk Anforderungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="010c9-118">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="010c9-119">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="010c9-119">Remarks</span></span>  
 <span data-ttu-id="010c9-120">Das- `add` Element fügt ein Authentifizierungs Modul am Ende der Liste registrierter Authentifizierungs Module hinzu.</span><span class="sxs-lookup"><span data-stu-id="010c9-120">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="010c9-121">Authentifizierungs Module werden in der Reihenfolge aufgerufen, in der Sie der Liste hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="010c9-121">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="010c9-122">Der Wert für das `type` -Attribut muss ein gültiger Typname und der zugehörige AssemblyName sein, getrennt durch ein Komma.</span><span class="sxs-lookup"><span data-stu-id="010c9-122">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="010c9-123">Konfigurationsdateien</span><span class="sxs-lookup"><span data-stu-id="010c9-123">Configuration Files</span></span>  
 <span data-ttu-id="010c9-124">Dieses Element kann in der Anwendungskonfigurationsdatei oder in der Computerkonfigurationsdatei ("Machine.config") verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="010c9-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="010c9-125">Beispiel</span><span class="sxs-lookup"><span data-stu-id="010c9-125">Example</span></span>  
 <span data-ttu-id="010c9-126">Im folgenden Beispiel werden die Standard Authentifizierungs Module aktiviert.</span><span class="sxs-lookup"><span data-stu-id="010c9-126">The following example enables the default authentication modules.</span></span> <span data-ttu-id="010c9-127">Sie sollten die Werte für Version und PublicKeyToken durch die korrekten Werte für das angegebene Modul ersetzen.</span><span class="sxs-lookup"><span data-stu-id="010c9-127">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
        <authenticationModules>  
            <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NegotiateClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.KerberosClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NtlmClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.BasicClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
        </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="010c9-128">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="010c9-128">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="010c9-129">Netzwerkeinstellungsschema</span><span class="sxs-lookup"><span data-stu-id="010c9-129">Network Settings Schema</span></span>](index.md)
