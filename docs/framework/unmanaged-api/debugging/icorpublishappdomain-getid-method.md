---
title: ICorPublishAppDomain::GetID-Methode
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetID
helpviewer_keywords:
- GetID method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetID method [.NET Framework debugging]
ms.assetid: 229437e3-1465-4bd8-8846-9804b2488133
topic_type:
- apiref
ms.openlocfilehash: 36c5c674f3cdf867107b9ee85a5befadc9246d78
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396302"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="a8508-102">ICorPublishAppDomain::GetID-Methode</span><span class="sxs-lookup"><span data-stu-id="a8508-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="a8508-103">Ruft den eindeutigen Bezeichner für diese [ICorPublishAppDomain](icorpublishappdomain-interface.md)ab.</span><span class="sxs-lookup"><span data-stu-id="a8508-103">Gets the unique identifier for this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8508-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a8508-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8508-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="a8508-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="a8508-106">vorgenommen Ein Zeiger auf den Bezeichner der Anwendungsdomäne.</span><span class="sxs-lookup"><span data-stu-id="a8508-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8508-107">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="a8508-107">Remarks</span></span>  
 <span data-ttu-id="a8508-108">Der Bezeichner ist nur im Gültigkeitsbereich des enthaltenden Prozesses eindeutig.</span><span class="sxs-lookup"><span data-stu-id="a8508-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8508-109">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="a8508-109">Requirements</span></span>  
 <span data-ttu-id="a8508-110">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8508-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8508-111">**Header:** Corpub. idl, Corpub. h</span><span class="sxs-lookup"><span data-stu-id="a8508-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a8508-112">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8508-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8508-113">**.NET Framework Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8508-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8508-114">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a8508-114">See also</span></span>

- [<span data-ttu-id="a8508-115">ICorPublishAppDomain-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="a8508-115">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
