---
title: Vordergrund- und Hintergrundthreads
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
ms.openlocfilehash: 5e7ec9e2c2a5ba3de1b4518cea15eb5f512640d3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279684"
---
# <a name="foreground-and-background-threads"></a>Vordergrund- und Hintergrundthreads
Ein verwalteter Thread ist entweder ein Hintergrund- oder Vordergrundthread. Hintergrundthreads sind mit einer Ausnahme identisch mit Vordergrundthreads: Ein Hintergrundthread erhält nicht die Ausführung der verwalteten Ausführungsumgebung aufrecht. Sobald alle Vordergrundthreads in einem verwalteten Prozess (wobei die EXE-Datei eine verwaltete Assembly ist) beendet sind, beendet das System alle Hintergrundthreads und fährt herunter.  
  
> [!NOTE]
> Wenn die Runtime einen Hintergrundthread beendet, da der Prozess heruntergefahren wird, wird keine Ausnahme im Thread ausgelöst. Wenn Threads allerdings beendet werden, da die <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType>-Methode die Anwendungsdomäne entlädt, wird eine <xref:System.Threading.ThreadAbortException> sowohl im Vordergrund- als auch Hintergrundthread ausgelöst.  
  
 Verwenden Sie die <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>-Eigenschaft, um zu bestimmen, ob ein Thread ein Hintergrund- oder Vordergrundthread ist, oder um seinen Status zu ändern. Ein Thread kann jederzeit durch Festlegen seiner <xref:System.Threading.Thread.IsBackground%2A>-Eigenschaft auf `true` in einen Hintergrundthread geändert werden.  
  
> [!IMPORTANT]
> Der Vorder- oder Hintergrundstatus eines Threads wirkt sich nicht auf das Ergebnis einer nicht behandelten Ausnahme im Thread aus. In .NET Framework Version 2.0 führt eine nicht behandelte Ausnahme in Vorder- oder Hintergrundthreads zum Beenden der Anwendung. Siehe [Ausnahmen in verwalteten Threads](exceptions-in-managed-threads.md).  
  
 Threads, die zum verwalteten Threadpool gehört (d.h. Threads, deren <xref:System.Threading.Thread.IsThreadPoolThread%2A>-Eigenschaft `true` ist), sind Hintergrundthreads. Alle Threads, die aus nicht verwaltetem Code in die verwaltete Ausführungsumgebung eingehen, werden als Hintergrundthreads markiert. Alle Threads, die durch Erstellen und Starten eines neuen <xref:System.Threading.Thread>-Objekts generiert werden, sind standardmäßig Vordergrundthreads.  
  
 Wenn Sie einen Thread zur Überwachung einer Aktivität, z.B. einer Socketverbindung, verwenden, legen Sie seine <xref:System.Threading.Thread.IsBackground%2A>-Eigenschaft auf `true` fest, sodass der Thread nicht das Beenden Ihres Prozesses verhindert.  
  
## <a name="see-also"></a>Weitere Informationen

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>
