---
title: CLRCreateInstance-Funktion
ms.date: 03/30/2017
api_name:
- CLRCreateInstance
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- CLRCreateInstance
helpviewer_keywords:
- CLRCreateInstance function [.NET Framework hosting]
ms.assetid: 5de13327-96c6-4697-a89e-b8bf40717855
topic_type:
- apiref
ms.openlocfilehash: 4aeacc718632c133550ed8de6649716c5d8b7423
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504442"
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="6063f-102">CLRCreateInstance-Funktion</span><span class="sxs-lookup"><span data-stu-id="6063f-102">CLRCreateInstance Function</span></span>
<span data-ttu-id="6063f-103">Bietet eine von drei Schnittstellen: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md)oder [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="6063f-103">Provides one of three interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6063f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6063f-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6063f-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="6063f-105">Parameters</span></span>  
 `clsid`  
 <span data-ttu-id="6063f-106">in Einer von drei Klassen Bezeichner: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy oder CLSID_CLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="6063f-106">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="6063f-107">in Einer von drei Schnittstellen Bezeichner (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy oder IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="6063f-107">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="6063f-108">vorgenommen Eine von drei Schnittstellen: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md)oder [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="6063f-108">[out] One of three interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6063f-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="6063f-109">Return Value</span></span>  
 <span data-ttu-id="6063f-110">Diese Methode gibt die folgenden spezifischen HRESULTs sowie HRESULT-Fehler zurück, die Methodenfehler anzeigen.</span><span class="sxs-lookup"><span data-stu-id="6063f-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6063f-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6063f-111">HRESULT</span></span>|<span data-ttu-id="6063f-112">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="6063f-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6063f-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="6063f-113">S_OK</span></span>|<span data-ttu-id="6063f-114">Die Methode wurde erfolgreich abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="6063f-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="6063f-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="6063f-115">E_POINTER</span></span>|<span data-ttu-id="6063f-116">`ppInterface` ist NULL.</span><span class="sxs-lookup"><span data-stu-id="6063f-116">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6063f-117">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="6063f-117">Remarks</span></span>  
 <span data-ttu-id="6063f-118">In der folgenden Tabelle werden die unterstützten Kombinationen für `clsid` und angezeigt `riid` .</span><span class="sxs-lookup"><span data-stu-id="6063f-118">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`clsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="6063f-119">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="6063f-119">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="6063f-120">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="6063f-120">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="6063f-121">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="6063f-121">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="6063f-122">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="6063f-122">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="6063f-123">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="6063f-123">CLSID_CLRDebugging</span></span>|<span data-ttu-id="6063f-124">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="6063f-124">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="6063f-125">Der folgende Code zeigt, wie verwendet wird `CLRCreateInstance` , um alle drei Schnittstellen zu erhalten:</span><span class="sxs-lookup"><span data-stu-id="6063f-125">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
```cpp  
#include <metahost.h>  
#pragma comment(lib, "mscoree.lib")  
  
ICLRMetaHost       *pMetaHost       = NULL;  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
ICLRDebugging      *pCLRDebugging   = NULL;  
HRESULT hr;  
hr = CLRCreateInstance(CLSID_CLRMetaHost, IID_ICLRMetaHost,  
                    (LPVOID*)&pMetaHost);  
hr = CLRCreateInstance (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  
                    (LPVOID*)&pMetaHostPolicy);  
hr = CLRCreateInstance (CLSID_CLRDebugging, IID_ICLRDebugging,  
                    (LPVOID*)&pCLRDebugging);  
```  
  
## <a name="requirements"></a><span data-ttu-id="6063f-126">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="6063f-126">Requirements</span></span>  
 <span data-ttu-id="6063f-127">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6063f-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6063f-128">**Header:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="6063f-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6063f-129">**Bibliothek:** Als Ressource in Mscoree. dll enthalten</span><span class="sxs-lookup"><span data-stu-id="6063f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6063f-130">**.NET Framework Versionen:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6063f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6063f-131">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="6063f-131">See also</span></span>

- [<span data-ttu-id="6063f-132">Hosting</span><span class="sxs-lookup"><span data-stu-id="6063f-132">Hosting</span></span>](index.md)
