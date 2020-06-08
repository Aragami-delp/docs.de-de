---
title: COR_PRF_GC_ROOT_KIND-Enumeration
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_KIND
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_KIND
helpviewer_keywords:
- COR_PRF_GC_ROOT_KIND enumeration [.NET Framework profiling]
ms.assetid: b9fb1c03-417f-41d4-aed4-02cb4ade8def
topic_type:
- apiref
ms.openlocfilehash: 0ea584bfff4340e5e9635d6c31e177e88765b582
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500870"
---
# <a name="cor_prf_gc_root_kind-enumeration"></a><span data-ttu-id="b6079-102">COR_PRF_GC_ROOT_KIND-Enumeration</span><span class="sxs-lookup"><span data-stu-id="b6079-102">COR_PRF_GC_ROOT_KIND Enumeration</span></span>
<span data-ttu-id="b6079-103">Gibt die Art des Garbage Collection Stamms an, der durch den Rückruf " [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) " verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="b6079-103">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6079-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b6079-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a><span data-ttu-id="b6079-105">Member</span><span class="sxs-lookup"><span data-stu-id="b6079-105">Members</span></span>  
  
|<span data-ttu-id="b6079-106">Member</span><span class="sxs-lookup"><span data-stu-id="b6079-106">Member</span></span>|<span data-ttu-id="b6079-107">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b6079-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|<span data-ttu-id="b6079-108">Der Stamm ist eine Variable auf dem Stapel.</span><span class="sxs-lookup"><span data-stu-id="b6079-108">The root is a variable on the stack.</span></span>|  
|`COR_PRF_GC_ROOT_FINALIZER`|<span data-ttu-id="b6079-109">Der Stamm ist ein Eintrag in der Finalizer-Warteschlange.</span><span class="sxs-lookup"><span data-stu-id="b6079-109">The root is an entry in the finalizer queue.</span></span>|  
|`COR_PRF_GC_ROOT_HANDLE`|<span data-ttu-id="b6079-110">Der Stamm ist ein Garbage Collection Handle.</span><span class="sxs-lookup"><span data-stu-id="b6079-110">The root is a garbage collection handle.</span></span>|  
|`COR_PRF_GC_ROOT_OTHER`|<span data-ttu-id="b6079-111">Die Art des Stamms ist nicht angegeben.</span><span class="sxs-lookup"><span data-stu-id="b6079-111">The kind of root is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b6079-112">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="b6079-112">Requirements</span></span>  
 <span data-ttu-id="b6079-113">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6079-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6079-114">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b6079-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b6079-115">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6079-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6079-116">**.NET Framework Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6079-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6079-117">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="b6079-117">See also</span></span>

- [<span data-ttu-id="b6079-118">Profilerstellungsenumerationen</span><span class="sxs-lookup"><span data-stu-id="b6079-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
