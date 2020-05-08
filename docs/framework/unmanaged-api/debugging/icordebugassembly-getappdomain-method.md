---
title: ICorDebugAssembly::GetAppDomain-Methode
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetAppDomain
helpviewer_keywords:
- ICorDebugAssembly::GetAppDomain method [.NET Framework debugging]
- GetAppDomain method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 14e18510-23ac-4cba-9f96-c86147a2df9d
topic_type:
- apiref
ms.openlocfilehash: 81936052c3fa2ad4fb77b503341b8b4873b80695
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894931"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="c1f88-102">ICorDebugAssembly::GetAppDomain-Methode</span><span class="sxs-lookup"><span data-stu-id="c1f88-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="c1f88-103">Ruft einen Schnittstellen Zeiger auf die Anwendungsdomäne ab, die `ICorDebugAssembly` diese Instanz enthält.</span><span class="sxs-lookup"><span data-stu-id="c1f88-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1f88-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c1f88-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1f88-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="c1f88-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="c1f88-106">vorgenommen Ein Zeiger auf die Adresse einer ICorDebugAppDomain-Schnittstelle, die die Anwendungsdomäne darstellt.</span><span class="sxs-lookup"><span data-stu-id="c1f88-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1f88-107">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c1f88-107">Remarks</span></span>  
 <span data-ttu-id="c1f88-108">Wenn diese Assembly die Systemassembly ist, `GetAppDomain` gibt NULL zurück.</span><span class="sxs-lookup"><span data-stu-id="c1f88-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1f88-109">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c1f88-109">Requirements</span></span>  
 <span data-ttu-id="c1f88-110">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1f88-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1f88-111">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c1f88-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1f88-112">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1f88-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1f88-113">**.NET Framework Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1f88-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
