---
title: ICorProfilerCallback::RuntimeThreadSuspended-Methode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadSuspended
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type:
- apiref
ms.openlocfilehash: 54f7dae511c8bf25dc96451e6477acf26655430a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503197"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="47a3d-102">ICorProfilerCallback::RuntimeThreadSuspended-Methode</span><span class="sxs-lookup"><span data-stu-id="47a3d-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="47a3d-103">Benachrichtigt den Profiler, dass der angegebene Thread angehalten wurde oder im Begriff ist, angehalten zu werden.</span><span class="sxs-lookup"><span data-stu-id="47a3d-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47a3d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="47a3d-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47a3d-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="47a3d-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="47a3d-106">in Die ID des Threads, der angehalten wurde.</span><span class="sxs-lookup"><span data-stu-id="47a3d-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47a3d-107">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="47a3d-107">Remarks</span></span>  
 <span data-ttu-id="47a3d-108">Die `RuntimeThreadSuspended` Benachrichtigung kann jederzeit zwischen den Callbacks [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) und zugeordneten [ICorProfilerCallback:: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) -Rückrufen erfolgen.</span><span class="sxs-lookup"><span data-stu-id="47a3d-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="47a3d-109">Benachrichtigungen zwischen [ICorProfilerCallback:: runtimesuspendend](icorprofilercallback-runtimesuspendfinished-method.md) und `RuntimeResumeStarted` sind für Threads vorgesehen, die in nicht verwaltetem Code ausgeführt wurden und bei einem Eintrag zur Laufzeit angehalten wurden.</span><span class="sxs-lookup"><span data-stu-id="47a3d-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="47a3d-110">Dieser Rückruf tritt im Allgemeinen auf, wenn ein Thread angehalten wird.</span><span class="sxs-lookup"><span data-stu-id="47a3d-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="47a3d-111">Wenn jedoch der derzeit ausgeführte Thread (der Thread, der diesen Rückruf aufgerufen hat) der Vorgang ist, der angehalten wird, wird dieser Rückruf unmittelbar vor dem Aussetzen des Threads ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="47a3d-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47a3d-112">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="47a3d-112">Requirements</span></span>  
 <span data-ttu-id="47a3d-113">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47a3d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47a3d-114">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="47a3d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="47a3d-115">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47a3d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47a3d-116">**.NET Framework Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47a3d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47a3d-117">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="47a3d-117">See also</span></span>

- [<span data-ttu-id="47a3d-118">ICorProfilerCallback-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="47a3d-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="47a3d-119">RuntimeThreadResumed-Methode</span><span class="sxs-lookup"><span data-stu-id="47a3d-119">RuntimeThreadResumed Method</span></span>](icorprofilercallback-runtimethreadresumed-method.md)
