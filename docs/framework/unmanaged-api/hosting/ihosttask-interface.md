---
title: IHostTask-Schnittstelle
ms.date: 03/30/2017
api_name:
- IHostTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask
helpviewer_keywords:
- IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type:
- apiref
ms.openlocfilehash: f8f476f681764a46700dd5ec83c8f9b2739f18f6
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842490"
---
# <a name="ihosttask-interface"></a>IHostTask-Schnittstelle
Stellt Methoden bereit, mit denen die Common Language Runtime (CLR) mit dem Host kommunizieren kann, um Aufgaben zu verwalten.  
  
## <a name="methods"></a>Methoden  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[Alert-Methode](ihosttask-alert-method.md)|Fordert an, dass der Host die Aufgabe reaktiviert, die von der aktuellen `IHostTask` Instanz dargestellt wird, sodass der Task abgebrochen werden kann.|  
|[GetPriority-Methode](ihosttask-getpriority-method.md)|Ruft die Thread Prioritäts Ebene der Aufgabe ab, die von der aktuellen-Instanz dargestellt wird `IHostTask` .|  
|[Join-Methode](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|Blockiert die aufrufende Aufgabe, bis die von der aktuellen Instanz dargestellte Aufgabe `IHostTask` abgeschlossen ist, das angegebene Zeitintervall abgelaufen ist oder [IHostTask:: Alert](ihosttask-alert-method.md) aufgerufen wird.|  
|[SetCLRTask-Methode](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|Ordnet der aktuellen Instanz eine [ICLRTask-Schnittstellen](iclrtask-interface.md) Instanz zu `IHostTask` .|  
|[SetPriority-Methode](ihosttask-setpriority-method.md)|Fordert an, dass der Host die Thread Prioritätsstufe für die Aufgabe anpasst, die durch die aktuelle Instanz dargestellt wird `IHostTask` .|  
|[Start-Methode](ihosttask-start-method.md)|Fordert an, dass der Host die von der aktuellen Instanz dargestellte Aufgabe von einem angehaltenen `IHostTask` Zustand in einen Live-Zustand verschiebt, in dem Code ausgeführt werden kann.|  
  
## <a name="remarks"></a>Hinweise  
 Die CLR ruft Methoden auf, die von definiert `IHostTask` werden, um eine Aufgabe zu starten, die Thread Prioritätsstufe festzulegen usw.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).  
  
 **Header:** Mscoree. h  
  
 **Bibliothek:** Als Ressource in Mscoree. dll enthalten  
  
 **.NET Framework Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch

- [ICLRTask-Schnittstelle](iclrtask-interface.md)
- [ICLRTaskManager-Schnittstelle](iclrtaskmanager-interface.md)
- [IHostTaskManager-Schnittstelle](ihosttaskmanager-interface.md)
- [Hostingschnittstellen](hosting-interfaces.md)
