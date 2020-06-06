---
title: Gclohthreshold-Element
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2020
ms.locfileid: "74451323"
---
# <a name="gclohthreshold-element"></a>Gclohthreshold-Element

Gibt die Schwellenwert Größe in Bytes an, die bewirkt, dass der Garbage Collector Objekte auf dem großen Objekt Heap (Loh) platziert.

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold>

## <a name="syntax"></a>Syntax

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|`enabled`|Erforderliches Attribut.<br /><br />Gibt den Schwellenwert an, der bewirkt, dass Objekte im großen Objekt Heap angezeigt werden.|

### <a name="enabled-attribute"></a>aktiviertes Attribut

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`nnnn`|Die Schwellenwert Größe in Byte, die bewirkt, dass Objekte auf dem großen Objekt Heap laufen.|

## <a name="child-elements"></a>Untergeordnete Elemente

Keine

## <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|`configuration`|Das Stammelement in jeder von den Common Language Runtime- und .NET Framework-Anwendungen verwendeten Konfigurationsdatei.|
|`runtime`|Enthält Informationen über die Assemblybindung und die Garbage Collection.|

## <a name="remarks"></a>Bemerkungen

Diese Einstellung wurde in .NET Framework 4,8 eingeführt.

## <a name="see-also"></a>Weitere Informationen

- [Schema für Lauf Zeit Einstellungen](index.md)
- [Schema der Konfigurationsdatei](../index.md)
- [Grundlagen der Garbage Collection](../../../../standard/garbage-collection/fundamentals.md)
- [Optionen für die .net Core-Laufzeitkonfiguration für GC](../../../../core/run-time-config/garbage-collector.md)
