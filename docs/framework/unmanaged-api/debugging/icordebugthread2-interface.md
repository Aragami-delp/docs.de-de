---
title: ICorDebugThread2-Schnittstelle
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
ms.openlocfilehash: a7a8d96548704f223f05826af79a4e227bdfab06
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379831"
---
# <a name="icordebugthread2-interface"></a><span data-ttu-id="720fd-102">ICorDebugThread2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="720fd-102">ICorDebugThread2 Interface</span></span>
<span data-ttu-id="720fd-103">Dient als logische Erweiterung der ICorDebugThread-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="720fd-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="720fd-104">Methoden</span><span class="sxs-lookup"><span data-stu-id="720fd-104">Methods</span></span>  
  
|<span data-ttu-id="720fd-105">Methode</span><span class="sxs-lookup"><span data-stu-id="720fd-105">Method</span></span>|<span data-ttu-id="720fd-106">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="720fd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="720fd-107">GetActiveFunctions-Methode</span><span class="sxs-lookup"><span data-stu-id="720fd-107">GetActiveFunctions Method</span></span>](icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="720fd-108">Ruft ein Array von COR_ACTIVE_FUNCTION-Instanzen ab, die Daten über die aktiven Funktionen in den Frames eines Threads enthalten.</span><span class="sxs-lookup"><span data-stu-id="720fd-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="720fd-109">GetConnectionID-Methode</span><span class="sxs-lookup"><span data-stu-id="720fd-109">GetConnectionID Method</span></span>](icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="720fd-110">Ruft einen Verbindungs Bezeichner für dieses ab `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="720fd-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="720fd-111">GetTaskID-Methode</span><span class="sxs-lookup"><span data-stu-id="720fd-111">GetTaskID Method</span></span>](icordebugthread2-gettaskid-method.md)|<span data-ttu-id="720fd-112">Ruft einen Aufgaben Bezeichner für dieses ab `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="720fd-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="720fd-113">GetVolatileOSThreadID-Methode</span><span class="sxs-lookup"><span data-stu-id="720fd-113">GetVolatileOSThreadID Method</span></span>](icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="720fd-114">Ruft den Thread Bezeichner des Betriebssystems für diesen ab `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="720fd-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="720fd-115">InterceptCurrentException-Methode</span><span class="sxs-lookup"><span data-stu-id="720fd-115">InterceptCurrentException Method</span></span>](icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="720fd-116">Ermöglicht einem Debugger das Abfangen der aktuellen Ausnahme in einem Thread.</span><span class="sxs-lookup"><span data-stu-id="720fd-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="720fd-117">Hinweise</span><span class="sxs-lookup"><span data-stu-id="720fd-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="720fd-118">Diese Schnittstelle kann weder computerübergreifend noch prozessübergreifend remote aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="720fd-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="720fd-119">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="720fd-119">Requirements</span></span>  
 <span data-ttu-id="720fd-120">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="720fd-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="720fd-121">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="720fd-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="720fd-122">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="720fd-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="720fd-123">**.NET Framework Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="720fd-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="720fd-124">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="720fd-124">See also</span></span>

- [<span data-ttu-id="720fd-125">Debugschnittstellen</span><span class="sxs-lookup"><span data-stu-id="720fd-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
