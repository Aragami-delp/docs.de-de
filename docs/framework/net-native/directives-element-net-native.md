---
title: <Directives>-Element (.net Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 0c6ebb8954e80f3f6dc6733f0e9d76094477689b
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202382"
---
# <a name="directives-element-net-native"></a>\<Directives>-Element (.net Native)
Das Stamm Element in jeder laufzeitdirektivendatei für .net Native.  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a>Syntax  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a>Attribute  
  
|Attribut|BESCHREIBUNG|  
|---------------|-----------------|  
|`xmlns`|Der XML-Namespace. Der Wert ist immer `http://schemas.microsoft.com/netfx/2013/01/metadata` .|  
  
## <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|Dient als Container für anwendungsweite Typen und Typmember, dessen Metadaten für die Reflektion verfügbar sind.|  
|[\<Library>](library-element-net-native.md)|Definiert die Assembly, deren untergeordneten Typen und Typmember Metadaten zur Laufzeit erfordern.|  
  
## <a name="remarks"></a>Hinweise  
 Jede Laufzeitanweisungsdatei darf nur ein `<Directives>`-Element enthalten.  
  
 Das `<Directives>` -Element kann NULL oder ein [\<Application>](application-element-net-native.md) -Element und NULL, ein oder mehrere- [\<Library>](library-element-net-native.md) Elemente enthalten.  
  
## <a name="see-also"></a>Siehe auch

- [Laufzeitanweisungs-Konfigurationsdatei (rd.xml) Referenz](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elemente der Laufzeitanweisung](runtime-directive-elements.md)
