---
title: <security>Element von<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: b85c54c6507313522286e0c66504cfd0c8afb2b0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738721"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a>\<security>Element von\<ws2007FederationHttpBinding>
Definiert die Sicherheitseinstellungen des [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) Elements.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/  Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               defaultProtectionLevel="none/sign/EncryptAndSign"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
  </binding>
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|attribute|BESCHREIBUNG|  
|---------------|-----------------|  
|`mode`|Optional. Gibt den angewendeten Sicherheitstyp an. Der Standardwert ist `Message`. Dieses Attribut ist vom Typ <xref:System.ServiceModel.WSFederationHttpSecurityMode>.|  
  
## <a name="mode-attribute"></a>mode-Attribut  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|Keine|Die SOAP-Nachricht ist während der Übertragung nicht sicher.|  
|`Message`|Integrität, Vertraulichkeit, Serverauthentifizierung und Clientauthentifizierung werden mittels SOAP-Nachrichtensicherheit bereitgestellt. Standardmäßig wird der Text verschlüsselt und signiert. Der Dienst muss mit einem Zertifikat konfiguriert werden. Die Clientauthentifizierung basiert auf dem Token, das von einem Sicherheitstokendienst für den Client ausgestellt wird.|  
|TransportWithMessageCredential|Integrität, Vertraulichkeit und Serverauthentifizierung werden über HTTPS bereitgestellt. Der Dienst muss mit einem Zertifikat konfiguriert werden. Die Clientauthentifizierung wird mittels SOAP-Nachrichtensicherheit bereitgestellt und basiert auf dem Token, das von einem Sicherheitstokendienst für den Client ausgestellt wird.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[\<message>](message-of-ws2007httpbinding.md)|Definiert die Einstellungen für die Sicherheit auf Nachrichtenebene. Dieses Element ist vom Typ <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|Definiert alle Bindungsfunktionen von [\<wsDualHttpBinding>](wsdualhttpbinding.md) .|  
  
## <a name="see-also"></a>Weitere Informationen

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [Vorgehensweise: Erstellen einer WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Sichern von Diensten und Clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [Wählen eines Typs von Anmeldeinformationen](../../../wcf/feature-details/selecting-a-credential-type.md)
- [Bindungen](../../../wcf/bindings.md)
- [Konfigurieren der vom System bereitgestellten Bindungen](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Verwenden von Bindungen, um Dienste und Clients zu konfigurieren](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
