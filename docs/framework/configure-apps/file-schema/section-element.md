---
title: <section> element
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
ms.openlocfilehash: 88f74c02ef627e9136e4437ffa150c36445266a3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153728"
---
# <a name="section-element"></a>\<section>-Element

Enthält eine Konfigurations Abschnitts Deklaration.

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

## <a name="syntax"></a>Syntax

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a>Erforderliche Attribute

|           | BESCHREIBUNG |
| --------- | ----------- |
| **name**  | Gibt den Namen des Konfigurations Abschnitts an. |
| **type**  | Gibt den Namen der Konfigurations Abschnitts-Handlerklasse an, die den Abschnitt aus der Konfigurationsdatei liest. Der Typwert weist die Syntax "vollständig qualifiziert-section-Handler-Class-Name, Simple-Assembly-Name" auf. Der einfache Assemblyname ist der Stamm Dateiname ohne die *dll* -Dateierweiterung. |

## <a name="optional-attributes"></a>Optionale Attribute

Die folgenden Attribute sind nur für ASP.NET-Anwendungen anwendbar. Das Konfigurationssystem ignoriert diese Attribute für andere Anwendungs Typen.

|                     | BESCHREIBUNG |
| ------------------- | ----------- |
| **AllowDefinition** | Gibt an, in welcher Konfigurationsdatei der Abschnitt verwendet werden kann. Verwenden Sie einen der folgenden Werte:<br><br>**Überall**<br>Ermöglicht die Verwendung des Abschnitts in jeder beliebigen Konfigurationsdatei. Dies ist die Standardeinstellung.<br>**MachineOnly**<br>Ermöglicht die Verwendung des Abschnitts nur in der Computer Konfigurationsdatei (*Machine. config*).<br>**MachineToApplication**<br>Ermöglicht die Verwendung des Abschnitts in der Computer Konfigurationsdatei oder der Anwendungs Konfigurationsdatei. |
| **AllowLocation**   | Bestimmt, ob der-Abschnitt innerhalb des-Elements verwendet werden kann **\<location>** . Verwenden Sie einen der folgenden Werte:<br><br>**true**<br>Ermöglicht die Verwendung des Abschnitts innerhalb des- **\<location>** Elements. Dies ist die Standardeinstellung.<br>**false**<br>Lässt nicht zu, dass der-Abschnitt innerhalb des-Elements verwendet wird **\<location>** . |

## <a name="parent-elements"></a>Übergeordnete Elemente

|     | BESCHREIBUNG |
| --- | ----------- |
| [**\<configSections>** Gewisses](configsections-element-for-configuration.md) | Enthält Konfigurations Abschnitts-und Namespace Deklarationen. |
| [**\<sectionGroup>** Gewisses](sectiongroup-element-for-configsections.md) | Definiert einen Namespace für Konfigurations Abschnitte. |

> [!NOTE]
> Ein- **\<section>** Element ist ein untergeordnetes Element von entweder **\<configSections>** oder, **\<sectionGroup>** aber nicht beides.

## <a name="child-elements"></a>Untergeordnete Elemente

Keine

## <a name="remarks"></a>Bemerkungen

Das Deklarieren eines Konfigurations Abschnitts definiert im Wesentlichen ein neues Element für die Konfigurationsdatei. Das neue-Element enthält die Einstellungen, die ein Konfigurations Abschnitts Handler (d. h. eine Klasse, die die- <xref:System.Configuration.IConfigurationSectionHandler> Schnittstelle implementiert) liest. Die Attribute und untergeordneten Elemente eines Abschnitts, den Sie definieren, sind von dem Abschnitts Handler abhängig, den Sie zum Lesen der Einstellungen verwenden.

Wenn Sie einen Konfigurations Abschnitts Handler in der Datei *Machine. config* deklarieren, können Sie den Konfigurations Abschnitt in jeder beliebigen Anwendungs Konfigurationsdatei auf diesem Computer verwenden, es sei denn, das **AllowDefinition** -Attribut gibt andernfalls an.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie ein Konfigurations Abschnitt definiert und Einstellungen für diesen Abschnitt definiert werden:

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler"
             allowLocation="false" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>Konfigurationsdatei

Dieses Element kann in der Anwendungs Konfigurationsdatei, in der Computer Konfigurationsdatei (*Machine. config*) und in den *Web. config* -Dateien verwendet werden, die sich nicht auf der Ebene des Anwendungs Verzeichnisses befinden.

## <a name="see-also"></a>Weitere Informationen

- [Konfigurationsdatei Schema für die .NET Framework](index.md)
