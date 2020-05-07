---
title: CreateCordbObject-Funktion
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
ms.openlocfilehash: 340d2de09562ea9b767203a7fa839cdc6b729b3b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860893"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="94e06-102">CreateCordbObject-Funktion</span><span class="sxs-lookup"><span data-stu-id="94e06-102">CreateCordbObject Function</span></span>
<span data-ttu-id="94e06-103">Erstellt eine Debugger-Schnittstelle ([ICorDebug](icordebug-interface.md)), die Funktionen zum Instanziieren einer verwalteten Debugsitzung für einen Remote Prozess bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="94e06-103">Creates a debugger interface ([ICorDebug](icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94e06-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="94e06-104">Syntax</span></span>  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94e06-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="94e06-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="94e06-106">[in] Debuggerversion des Zielprozesses.</span><span class="sxs-lookup"><span data-stu-id="94e06-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="94e06-107">Dieser Parameter muss CorDebugVersion_2_0 für das Remotedebuggen sein.</span><span class="sxs-lookup"><span data-stu-id="94e06-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="94e06-108">vorgenommen Zeiger auf einen Zeiger auf ein Objekt, das in eine [ICorDebug](icordebug-interface.md) -Schnittstelle umgewandelt und zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="94e06-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94e06-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="94e06-109">Return Value</span></span>  
 <span data-ttu-id="94e06-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="94e06-110">S_OK</span></span>  
 <span data-ttu-id="94e06-111">Die Anzahl der CLRs im Prozess wurde erfolgreich ermittelt, und das entsprechende Handle und die Pfadarrays wurden ordnungsgemäß aufgefüllt.</span><span class="sxs-lookup"><span data-stu-id="94e06-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="94e06-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="94e06-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="94e06-113">`ppCordb` ist NULL, oder `iDebuggerVersion` ist nicht CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="94e06-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="94e06-114">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="94e06-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="94e06-115">Für `ppCordb` kann nicht genug Arbeitspeicher zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="94e06-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="94e06-116">E_FAIL (oder andere E_-Rückgabecodes)</span><span class="sxs-lookup"><span data-stu-id="94e06-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="94e06-117">Andere Fehler.</span><span class="sxs-lookup"><span data-stu-id="94e06-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94e06-118">Hinweise</span><span class="sxs-lookup"><span data-stu-id="94e06-118">Remarks</span></span>  
 <span data-ttu-id="94e06-119">Die [ICorDebug](icordebug-interface.md) -Schnittstelle, die `ppCordb` in zurückgegeben wird, ist die Debugschnittstelle der obersten Ebene für alle verwalteten Debugdienste.</span><span class="sxs-lookup"><span data-stu-id="94e06-119">The [ICorDebug](icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94e06-120">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="94e06-120">Requirements</span></span>  
 <span data-ttu-id="94e06-121">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94e06-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94e06-122">**Header:** Coreclrremotedebugginginterfaces. h</span><span class="sxs-lookup"><span data-stu-id="94e06-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="94e06-123">**Bibliothek:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="94e06-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="94e06-124">**.NET Framework Versionen:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="94e06-124">**.NET Framework Versions:** 3.5 SP1</span></span>
