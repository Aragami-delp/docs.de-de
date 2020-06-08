---
title: ICorProfilerCallback::ClassLoadStarted-Methode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type:
- apiref
ms.openlocfilehash: 9a9fdc80c8f63dd5b004953266a5d7399655bc71
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500363"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="461b7-102">ICorProfilerCallback::ClassLoadStarted-Methode</span><span class="sxs-lookup"><span data-stu-id="461b7-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="461b7-103">Benachrichtigt den Profiler, dass eine Klasse geladen wird.</span><span class="sxs-lookup"><span data-stu-id="461b7-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="461b7-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="461b7-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="461b7-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="461b7-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="461b7-106">\[in] identifiziert die Klasse, die geladen wird.</span><span class="sxs-lookup"><span data-stu-id="461b7-106">\[in] Identifies the class that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="461b7-107">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="461b7-107">Remarks</span></span>  
 <span data-ttu-id="461b7-108">Der Wert von `classId` ist für eine Informationsanforderung erst gültig, wenn die [ICorProfilerCallback:: classloadabgeschlossene](icorprofilercallback-classloadfinished-method.md) -Methode aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="461b7-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="461b7-109">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="461b7-109">Requirements</span></span>  
 <span data-ttu-id="461b7-110">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="461b7-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="461b7-111">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="461b7-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="461b7-112">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="461b7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="461b7-113">**.NET Framework Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="461b7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="461b7-114">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="461b7-114">See also</span></span>

- [<span data-ttu-id="461b7-115">ICorProfilerCallback-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="461b7-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
