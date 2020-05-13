---
title: ICorDebugILFrame4::EnumerateLocalVariablesEx-Methode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type:
- apiref
ms.openlocfilehash: aef28af3eff6aba03003f156b9226b61a8e72d5b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213750"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="bdee3-102">ICorDebugILFrame4::EnumerateLocalVariablesEx-Methode</span><span class="sxs-lookup"><span data-stu-id="bdee3-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>
<span data-ttu-id="bdee3-103">[Wird nur in .NET Framework 4.5.2 und neueren Versionen unterstützt]</span><span class="sxs-lookup"><span data-stu-id="bdee3-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="bdee3-104">Ruft einen Enumerator für die lokale Variable im Rahmen ab, und schließt optional Variablen ein, die in der Profiler-ReJIT-Instrumentation hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="bdee3-104">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdee3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bdee3-105">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdee3-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="bdee3-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="bdee3-107">in Ein [ilcodekind](ilcodekind-enumeration.md) -Enumerationsmember, der angibt, ob in der Profiler-ReJIT-Instrumentation hinzugefügte Variablen in den Frame eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="bdee3-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="bdee3-108">vorgenommen Ein Zeiger auf die Adresse eines ICorDebugValueEnum-Objekts, bei dem es sich um den Enumerator für die lokalen Variablen in diesem Frame handelt.</span><span class="sxs-lookup"><span data-stu-id="bdee3-108">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdee3-109">Hinweise</span><span class="sxs-lookup"><span data-stu-id="bdee3-109">Remarks</span></span>  
 <span data-ttu-id="bdee3-110">Diese Methode ähnelt der [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md) -Methode, außer dass Sie optional auf Variablen zugreift, die in der Profiler-ReJIT-Instrumentierung hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="bdee3-110">This method is similar to the [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="bdee3-111">Das Festlegen `flags` von auf `ILCODE_ORIGINAL_IL` entspricht dem Aufrufen von [ICorDebugILFrame:: EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md).</span><span class="sxs-lookup"><span data-stu-id="bdee3-111">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="bdee3-112">Die Einstellung von `flags` auf `ILCODE_REJIT_IL` ermöglicht dem Debugger Zugriff auf die lokalen Variablen, die in der Profiler-ReJIT-Instrumentierung hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="bdee3-112">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="bdee3-113">Ist die Intermediate Language (IL) nicht instrumentiert, ist die Enumeration leer und die Methode gibt `S_OK` zurück.</span><span class="sxs-lookup"><span data-stu-id="bdee3-113">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="bdee3-114">Der Enumerator schließt möglicherweise nicht alle lokalen Variablen in die ausgeführte Methode ein, da einige von ihnen möglicherweise nicht aktiv sind.</span><span class="sxs-lookup"><span data-stu-id="bdee3-114">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdee3-115">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="bdee3-115">Requirements</span></span>  
 <span data-ttu-id="bdee3-116">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdee3-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdee3-117">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bdee3-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdee3-118">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdee3-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdee3-119">**.NET Framework Versionen:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdee3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdee3-120">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="bdee3-120">See also</span></span>

- [<span data-ttu-id="bdee3-121">ICorDebugILFrame4-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="bdee3-121">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="bdee3-122">Debugschnittstellen</span><span class="sxs-lookup"><span data-stu-id="bdee3-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="bdee3-123">ReJIT: Anleitung</span><span class="sxs-lookup"><span data-stu-id="bdee3-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
