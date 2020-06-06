---
title: <remove>-Element für <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
ms.openlocfilehash: 83abbdbf0d3e4dfd16c0e8c649200c4ecc7329f7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215492"
---
# <a name="remove-element-for-appsettings"></a>\<remove>-Element für \<appSettings>

Entfernt benutzerdefinierte Anwendungseinstellungen.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a>Syntax

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a>attribute

|         | BESCHREIBUNG |
| ------- | ----------- |
| **key** | Erforderliches Attribut.<br><br>Gibt den Namen des zu entfernenden Schlüssels an. |

### <a name="parent-element"></a>Übergeordnetes Element

|     | BESCHREIBUNG |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | Dieses Thema enthält benutzerdefinierte Anwendungseinstellungen, z.B. Dateipfade, URLs für den XML-Webdienst oder andere benutzerdefinierte Konfigurationsinformationen für eine Anwendung. |

## <a name="child-elements"></a>Untergeordnete Elemente

Keine

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie eine benutzerdefinierte Konfigurationseinstellung für entfernt wird `ApplicationName` :

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a>Weitere Informationen

- [Konfigurationsdatei Schema für die .NET Framework](../index.md)
