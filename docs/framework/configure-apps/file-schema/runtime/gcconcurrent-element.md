---
title: gcConcurrent-Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 249518ae7477d284d50f9010757db83b7752c657
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102917"
---
# <a name="gcconcurrent-element"></a>\<gcConcurrent>-Element

Gibt an, ob die Common Language Runtime die Garbage Collection auf einem separaten Thread ausführt.

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent>

## <a name="syntax"></a>Syntax

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|`enabled`|Erforderliches Attribut.<br /><br />Gibt an, ob die Runtime die Garbage Collection gleichzeitig ausführt.|

#### <a name="enabled-attribute"></a>aktiviertes Attribut

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`false`|Wird Garbage Collection nicht gleichzeitig ausgeführt.|
|`true`|Die Garbage Collection wird gleichzeitig ausgeführt. Dies ist die Standardeinstellung.|

### <a name="child-elements"></a>Untergeordnete Elemente

Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|`configuration`|Das Stammelement in jeder von den Common Language Runtime- und .NET Framework-Anwendungen verwendeten Konfigurationsdatei.|
|`runtime`|Enthält Informationen über die Assemblybindung und die Garbage Collection.|

## <a name="remarks"></a>Bemerkungen

Vor .NET Framework 4 Garbage Collection die Arbeitsstation gleichzeitige Garbage Collection unterstützt, die Garbage Collection im Hintergrund auf einem separaten Thread ausgeführt hat. In .NET Framework 4 wurde die gleichzeitige Garbage Collection durch den Background-GC ersetzt, der auch Garbage Collection im Hintergrund in einem separaten Thread ausführt. Ab .NET Framework 4,5 wurde die Hintergrund Sammlung in Server Garbage Collection verfügbar. Das **gcConcurrent** -Element steuert, ob die Laufzeit entweder gleichzeitige oder Hintergrund Garbage Collection ausführt, wenn Sie verfügbar ist, oder ob Sie im Vordergrund Garbage Collection ausführt.

### <a name="to-disable-background-garbage-collection"></a>So deaktivieren Sie Hintergrund Garbage Collection

> [!WARNING]
> Beginnend mit .NET Framework 4 wird die gleichzeitige Garbage Collection durch Hintergrund Garbage Collection ersetzt. Die Begriffe " *parallel* " und " *Background* " werden in der .NET Framework-Dokumentation austauschbar verwendet. Um die Hintergrund Garbage Collection zu deaktivieren, verwenden Sie das **gcConcurrent** -Element, wie in diesem Artikel erläutert.

Standardmäßig verwendet die Runtime gleichzeitige Garbage Collection oder Garbage Collection im Hintergrund, die für Wartezeiten optimiert ist. Wenn Ihre Anwendung intensive Benutzerinteraktion bedingt, belassen Sie die parallele Garbage Collection aktiviert, damit die Pausenzeiten der Anwendung für die Ausführung der Garbage Collection minimiert werden. Wenn Sie das- `enabled` Attribut des **gcConcurrent** -Elements auf festlegen `false` , verwendet die Common Language Runtime nicht gleichzeitige Garbage Collection, die für den Durchsatz optimiert ist.

Mit der folgenden Konfigurationsdatei wird die Hintergrund Garbage Collection deaktiviert:

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

Wenn eine **gcconcurrentsetting** -Einstellung in der Computer Konfigurationsdatei vorhanden ist, wird der Standardwert für alle .NET Framework Anwendungen definiert. Die Einstellung in der Computerkonfigurationsdatei setzt die Einstellung in der Anwendungskonfigurationsdatei außer Kraft.

Weitere Informationen zu gleichzeitigen und Hintergrund Garbage Collection finden Sie unter [Hintergrund Garbage Collection](../../../../standard/garbage-collection/background-gc.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden Hintergrund Garbage Collection aktiviert:

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Weitere Informationen

- [Schema für Laufzeiteinstellungen](index.md)
- [Konfigurationsdateischema](../index.md)
- [Grundlagen der Garbage Collection](../../../../standard/garbage-collection/fundamentals.md)
