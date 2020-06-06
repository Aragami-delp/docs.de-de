---
title: gcserver-Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
ms.openlocfilehash: 8eab5e36bab90510aff4f1a3e15328197ac59ed7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968950"
---
# <a name="gcserver-element"></a><span data-ttu-id="cacce-102">\<gcServer>-Element</span><span class="sxs-lookup"><span data-stu-id="cacce-102">\<gcServer> element</span></span>

<span data-ttu-id="cacce-103">Gibt an, ob die Common Language Runtime die Garbage Collection auf dem Server ausführt.</span><span class="sxs-lookup"><span data-stu-id="cacce-103">Specifies whether the common language runtime runs server garbage collection.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer>

## <a name="syntax"></a><span data-ttu-id="cacce-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="cacce-104">Syntax</span></span>

```xml
<gcServer
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cacce-105">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="cacce-105">Attributes and elements</span></span>

<span data-ttu-id="cacce-106">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="cacce-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="cacce-107">Attribute</span><span class="sxs-lookup"><span data-stu-id="cacce-107">Attributes</span></span>

|<span data-ttu-id="cacce-108">attribute</span><span class="sxs-lookup"><span data-stu-id="cacce-108">Attribute</span></span>|<span data-ttu-id="cacce-109">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="cacce-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="cacce-110">Erforderliches Attribut.</span><span class="sxs-lookup"><span data-stu-id="cacce-110">Required attribute.</span></span><br /><br /><span data-ttu-id="cacce-111">Gibt an, ob die Runtime die Garbage Collection auf dem Server ausführt.</span><span class="sxs-lookup"><span data-stu-id="cacce-111">Specifies whether the runtime runs server garbage collection.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="cacce-112">aktiviertes Attribut</span><span class="sxs-lookup"><span data-stu-id="cacce-112">enabled attribute</span></span>

|<span data-ttu-id="cacce-113">Wert</span><span class="sxs-lookup"><span data-stu-id="cacce-113">Value</span></span>|<span data-ttu-id="cacce-114">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="cacce-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="cacce-115">Die Garbage Collection wird nicht auf dem Server ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="cacce-115">Does not run server garbage collection.</span></span> <span data-ttu-id="cacce-116">Dies ist die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="cacce-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="cacce-117">Die Garbage Collection wird auf dem Server ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="cacce-117">Runs server garbage collection.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="cacce-118">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="cacce-118">Child elements</span></span>

<span data-ttu-id="cacce-119">Keine</span><span class="sxs-lookup"><span data-stu-id="cacce-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cacce-120">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="cacce-120">Parent elements</span></span>

|<span data-ttu-id="cacce-121">Element</span><span class="sxs-lookup"><span data-stu-id="cacce-121">Element</span></span>|<span data-ttu-id="cacce-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="cacce-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="cacce-123">Das Stammelement in jeder von den Common Language Runtime- und .NET Framework-Anwendungen verwendeten Konfigurationsdatei.</span><span class="sxs-lookup"><span data-stu-id="cacce-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="cacce-124">Enthält Informationen über die Assemblybindung und die Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="cacce-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cacce-125">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="cacce-125">Remarks</span></span>

<span data-ttu-id="cacce-126">Die Common Language Runtime (CLR) unterstützt zwei Arten der Garbage Collection: die Garbage Collection auf der Arbeitsstation, die auf allen Systemen verfügbar ist, und die Garbage Collection auf dem Server, die auf Systemen mit mehreren Prozessoren verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="cacce-126">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="cacce-127">Verwenden Sie das **gcserver** -Element, um den Typ des Garbage Collection zu steuern, den die CLR ausführt.</span><span class="sxs-lookup"><span data-stu-id="cacce-127">Use the **gcServer** element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="cacce-128">Mithilfe der <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>-Eigenschaft können Sie bestimmen, ob die Garbage Collection auf dem Server aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="cacce-128">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>

<span data-ttu-id="cacce-129">Für Computer mit einem Prozessor stellt die Garbage Collection auf der Arbeitsstation (Standardeinstellung) in der Regel die schnellste Lösung dar.</span><span class="sxs-lookup"><span data-stu-id="cacce-129">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="cacce-130">Auf Computern mit zwei Prozessoren kann die Arbeitsstation- oder die Serveroption verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="cacce-130">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="cacce-131">Sind mehr als zwei Prozessoren vorhanden, stellt die Garbage Collection auf dem Server in der Regel die schnellste Lösung dar.</span><span class="sxs-lookup"><span data-stu-id="cacce-131">Server garbage collection should be the fastest option for more than two processors.</span></span> <span data-ttu-id="cacce-132">In den meisten Fällen deaktivieren Multiprozessor-Serversysteme die Server-GC und verwenden stattdessen die Arbeitsstations-GC, wenn viele Instanzen einer Server-App auf dem gleichen Computer ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="cacce-132">Most commonly, multiprocessor server systems disable server GC and use workstation GC instead when many instances of a server app run on the same machine.</span></span>

<span data-ttu-id="cacce-133">Dieses Element kann nur in der Anwendungskonfigurationsdatei verwendet werden. Wenn es in der Computerkonfigurationsdatei enthalten ist, wird es ignoriert.</span><span class="sxs-lookup"><span data-stu-id="cacce-133">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="cacce-134">In .NET Framework 4 und früheren Versionen ist die gleichzeitige Garbage Collection nicht verfügbar, wenn die Garbage Collection auf dem Server aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="cacce-134">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="cacce-135">Beginnend mit dem .NET Framework 4,5 ist der Server Garbage Collection gleichzeitig.</span><span class="sxs-lookup"><span data-stu-id="cacce-135">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="cacce-136">Um nicht gleichzeitige Server Garbage Collection zu verwenden, legen Sie das **gcserver** -Element auf `true` und das [gcConcurrent-Element](gcconcurrent-element.md) auf fest `false` .</span><span class="sxs-lookup"><span data-stu-id="cacce-136">To use non-concurrent server garbage collection, set the **gcServer** element to `true` and the [gcConcurrent element](gcconcurrent-element.md) to `false`.</span></span>

<span data-ttu-id="cacce-137">Ab .NET Framework 4.6.2 können Sie auch die folgenden Elemente verwenden, um Server GC zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="cacce-137">Starting with .NET Framework 4.6.2, you can also use the following elements to configure server GC:</span></span>

- <span data-ttu-id="cacce-138">[Gcnoaffinitize](gcnoaffinitize-element.md): gibt an, ob zwischen Server-GC-Heaps und Prozessoren eine Affinität besteht.</span><span class="sxs-lookup"><span data-stu-id="cacce-138">[GCNoAffinitize](gcnoaffinitize-element.md), which specifies whether there is an affinity between server GC heaps and processors.</span></span> <span data-ttu-id="cacce-139">Standardmäßig ist für jeden Prozessor ein Server-GC-Heap vorhanden.</span><span class="sxs-lookup"><span data-stu-id="cacce-139">By default, there is one server GC heap for each processor.</span></span>

- <span data-ttu-id="cacce-140">[Gcheapcount](gcheapcount-element.md): schränkt die Anzahl von Heaps ein, die von einem Prozess verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="cacce-140">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by a process.</span></span>

- <span data-ttu-id="cacce-141">[Gcheapaffinitizemask](gcheapaffinitizemask-element.md): definiert die Affinität zwischen den verfügbaren Server-GC-Heaps und einzelnen Prozessoren.</span><span class="sxs-lookup"><span data-stu-id="cacce-141">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which defines the affinity between the available server GC heaps and individual processors.</span></span>

## <a name="example"></a><span data-ttu-id="cacce-142">Beispiel</span><span class="sxs-lookup"><span data-stu-id="cacce-142">Example</span></span>

<span data-ttu-id="cacce-143">Im folgenden Beispiel wird die Server Garbage Collection aktiviert:</span><span class="sxs-lookup"><span data-stu-id="cacce-143">The following example enables server garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="cacce-144">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="cacce-144">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="cacce-145">Schema für Laufzeiteinstellungen</span><span class="sxs-lookup"><span data-stu-id="cacce-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cacce-146">Konfigurationsdateischema</span><span class="sxs-lookup"><span data-stu-id="cacce-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="cacce-147">So deaktivieren Sie die parallele Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="cacce-147">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
