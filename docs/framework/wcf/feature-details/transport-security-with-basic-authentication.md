---
title: Transportsicherheit mit Standardauthentifizierung
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: 7c83de70e404fe8304bc2e35c1bb5df9e42f95b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576095"
---
# <a name="transport-security-with-basic-authentication"></a><span data-ttu-id="2d65f-102">Transportsicherheit mit Standardauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="2d65f-102">Transport Security with Basic Authentication</span></span>
<span data-ttu-id="2d65f-103">Die folgende Abbildung zeigt einen Windows Communication Foundation (WCF)-Dienst und-Client.</span><span class="sxs-lookup"><span data-stu-id="2d65f-103">The following illustration shows a Windows Communication Foundation (WCF) service and client.</span></span> <span data-ttu-id="2d65f-104">Der Server benötigt ein gültiges X.509-Zertifikat, das für Secure Sockets Layer (SSL) verwendet werden kann, und die Clients müssen das Zertifikat des Servers als vertrauenswürdig ansehen.</span><span class="sxs-lookup"><span data-stu-id="2d65f-104">The server needs a valid X.509 certificate that can be used for Secure Sockets Layer (SSL), and the clients must trust the server’s certificate.</span></span> <span data-ttu-id="2d65f-105">Außerdem verfügt der Webdienst bereits über eine SSL-Implementierung, die Sie verwenden können.</span><span class="sxs-lookup"><span data-stu-id="2d65f-105">Further, the Web service already has an SSL implementation that can be used.</span></span> <span data-ttu-id="2d65f-106">Weitere Informationen zum Aktivieren der Standard Authentifizierung für Internetinformationsdienste (IIS) finden Sie unter <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication> .</span><span class="sxs-lookup"><span data-stu-id="2d65f-106">For more information about enabling basic authentication on Internet Information Services (IIS), see <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>.</span></span>  
  
 ![Screenshot, der die Transportsicherheit mit Standard Authentifizierung anzeigt.](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|<span data-ttu-id="2d65f-108">Merkmal</span><span class="sxs-lookup"><span data-stu-id="2d65f-108">Characteristic</span></span>|<span data-ttu-id="2d65f-109">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="2d65f-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="2d65f-110">Sicherheitsmodus</span><span class="sxs-lookup"><span data-stu-id="2d65f-110">Security Mode</span></span>|<span data-ttu-id="2d65f-111">Transport</span><span class="sxs-lookup"><span data-stu-id="2d65f-111">Transport</span></span>|  
|<span data-ttu-id="2d65f-112">Interoperabilität</span><span class="sxs-lookup"><span data-stu-id="2d65f-112">Interoperability</span></span>|<span data-ttu-id="2d65f-113">Mit vorhandenen Webdienstclients und Diensten</span><span class="sxs-lookup"><span data-stu-id="2d65f-113">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="2d65f-114">Authentifizierung (Server)</span><span class="sxs-lookup"><span data-stu-id="2d65f-114">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="2d65f-115">Authentifizierung (Client)</span><span class="sxs-lookup"><span data-stu-id="2d65f-115">Authentication (Client)</span></span>|<span data-ttu-id="2d65f-116">Ja (mithilfe von HTTPS)</span><span class="sxs-lookup"><span data-stu-id="2d65f-116">Yes (using HTTPS)</span></span><br /><br /> <span data-ttu-id="2d65f-117">Ja (mithilfe von Benutzername/Kennwort)</span><span class="sxs-lookup"><span data-stu-id="2d65f-117">Yes (through User name/Password)</span></span>|  
|<span data-ttu-id="2d65f-118">Integrität</span><span class="sxs-lookup"><span data-stu-id="2d65f-118">Integrity</span></span>|<span data-ttu-id="2d65f-119">Ja</span><span class="sxs-lookup"><span data-stu-id="2d65f-119">Yes</span></span>|  
|<span data-ttu-id="2d65f-120">Vertraulichkeit</span><span class="sxs-lookup"><span data-stu-id="2d65f-120">Confidentiality</span></span>|<span data-ttu-id="2d65f-121">Ja</span><span class="sxs-lookup"><span data-stu-id="2d65f-121">Yes</span></span>|  
|<span data-ttu-id="2d65f-122">Transport</span><span class="sxs-lookup"><span data-stu-id="2d65f-122">Transport</span></span>|<span data-ttu-id="2d65f-123">HTTPS</span><span class="sxs-lookup"><span data-stu-id="2d65f-123">HTTPS</span></span>|  
|<span data-ttu-id="2d65f-124">Bindung</span><span class="sxs-lookup"><span data-stu-id="2d65f-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="2d65f-125">Dienst</span><span class="sxs-lookup"><span data-stu-id="2d65f-125">Service</span></span>  
 <span data-ttu-id="2d65f-126">Der folgende Code und die folgende Konfiguration werden unabhängig voneinander ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="2d65f-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="2d65f-127">Führen Sie einen der folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="2d65f-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="2d65f-128">Erstellen Sie einen separaten Dienst, indem Sie den Code ohne Konfiguration verwenden.</span><span class="sxs-lookup"><span data-stu-id="2d65f-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="2d65f-129">Erstellen Sie mit der angegebenen Konfiguration einen Dienst, aber definieren Sie keine Endpunkte.</span><span class="sxs-lookup"><span data-stu-id="2d65f-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2d65f-130">Code</span><span class="sxs-lookup"><span data-stu-id="2d65f-130">Code</span></span>  
 <span data-ttu-id="2d65f-131">Der folgende Code zeigt, wie Sie einen Dienstendpunkt erstellen, der zur Sicherstellung der Übertragungssicherheit einen Benutzernamen und ein Kennwort für die Windows-Domäne verwendet.</span><span class="sxs-lookup"><span data-stu-id="2d65f-131">The following code shows how to create a service endpoint that uses a Windows domain user name and password for transfer security.</span></span> <span data-ttu-id="2d65f-132">Beachten Sie, dass der Dienst ein X.509-Zertifikat erfordert, um den Client zu authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="2d65f-132">Note that the service requires an X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="2d65f-133">Weitere Informationen finden Sie unter [Arbeiten mit Zertifikaten](working-with-certificates.md) und Gewusst [wie: Konfigurieren eines Ports mit einem SSL-Zertifikat](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="2d65f-133">For more information, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a><span data-ttu-id="2d65f-134">Konfiguration</span><span class="sxs-lookup"><span data-stu-id="2d65f-134">Configuration</span></span>  
 <span data-ttu-id="2d65f-135">Der folgende Code konfiguriert einen Dienst, um die Standardauthentifizierung mit der Sicherheit auf Transportebene zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="2d65f-135">The following configures a service to use basic authentication with transport-level security:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding name="UsernameWithTransport">  
                    <security mode="Transport">  
                        <transport clientCredentialType="Basic" />  
                    </security>  
                </binding>  
            </wsHttpBinding>  
        </bindings>  
        <services>  
            <service name="BasicAuthentication.Calculator">  
                <endpoint address="https://localhost/Calculator"  
                          binding="wsHttpBinding"
                          bindingConfiguration="UsernameWithTransport"  
                          name="BasicEndpoint"
                          contract="BasicAuthentication.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="2d65f-136">Client</span><span class="sxs-lookup"><span data-stu-id="2d65f-136">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="2d65f-137">Code</span><span class="sxs-lookup"><span data-stu-id="2d65f-137">Code</span></span>  
 <span data-ttu-id="2d65f-138">Der folgende Code zeigt den Clientcode, der den Benutzernamen und das Kennwort enthält.</span><span class="sxs-lookup"><span data-stu-id="2d65f-138">The following code shows the client code that includes the user name and password.</span></span> <span data-ttu-id="2d65f-139">Beachten Sie, dass der Benutzer einen gültigen Windows-Benutzernamen und ein Kennwort angeben muss.</span><span class="sxs-lookup"><span data-stu-id="2d65f-139">Note that the user must provide a valid Windows user name and password.</span></span> <span data-ttu-id="2d65f-140">Der Code zum Zurückgeben des Benutzernamens und des Kennworts ist hier nicht gezeigt.</span><span class="sxs-lookup"><span data-stu-id="2d65f-140">The code to return the user name and password is not shown here.</span></span> <span data-ttu-id="2d65f-141">Verwenden Sie ein Dialogfeld oder ein anderes Oberflächenelement, um die Informationen vom Benutzer abzufragen.</span><span class="sxs-lookup"><span data-stu-id="2d65f-141">Use a dialog box or other interface to query the user for the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d65f-142">Sie können den Benutzernamen und das Kennwort nur mithilfe von Code festlegen.</span><span class="sxs-lookup"><span data-stu-id="2d65f-142">User name and password can only be set using code.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="2d65f-143">Konfiguration</span><span class="sxs-lookup"><span data-stu-id="2d65f-143">Configuration</span></span>  
 <span data-ttu-id="2d65f-144">Der folgende Code zeigt die Clientkonfiguration.</span><span class="sxs-lookup"><span data-stu-id="2d65f-144">The following code shows the client configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d65f-145">Sie können die Konfiguration nicht verwenden, um den Benutzernamen und das Kennwort festzulegen.</span><span class="sxs-lookup"><span data-stu-id="2d65f-145">You cannot use configuration to set the user name and password.</span></span> <span data-ttu-id="2d65f-146">Die hier gezeigte Konfiguration muss mithilfe von Code erweitert werden, um den Benutzernamen und das Kennwort festzulegen.</span><span class="sxs-lookup"><span data-stu-id="2d65f-146">The configuration shown here must be augmented using code to set the user name and password.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Basic" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d65f-147">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2d65f-147">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [<span data-ttu-id="2d65f-148">Verwenden von Zertifikaten</span><span class="sxs-lookup"><span data-stu-id="2d65f-148">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="2d65f-149">Vorgehensweise: Konfigurieren eines Anschlusses mit einem SSL-Zertifikat</span><span class="sxs-lookup"><span data-stu-id="2d65f-149">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="2d65f-150">Sicherheitsübersicht</span><span class="sxs-lookup"><span data-stu-id="2d65f-150">Security Overview</span></span>](security-overview.md)
- [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md)
- <span data-ttu-id="2d65f-151">[Sicherheitsmodell für Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="2d65f-151">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
