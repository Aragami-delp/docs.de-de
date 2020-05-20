---
title: ICLRRuntimeInfo::GetInterface-Methode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetInterface
helpviewer_keywords:
- GetInterface method [.NET Framework hosting]
- ICLRRuntimeInfo::GetInterface method [.NET Framework hosting]
ms.assetid: cc7b0e5b-48c3-4509-8ebb-611ddb1f7ec2
topic_type:
- apiref
ms.openlocfilehash: c8ac959c192814562488ab916c8462b0baa0d8e6
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703646"
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="89a7b-102">ICLRRuntimeInfo::GetInterface-Methode</span><span class="sxs-lookup"><span data-stu-id="89a7b-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="89a7b-103">Lädt die CLR in den aktuellen Prozess und gibt Lauf Zeit Schnittstellen Zeiger zurück, z. [b. ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)und [IMetaDataDispenserEx](../metadata/imetadatadispenser-interface.md).</span><span class="sxs-lookup"><span data-stu-id="89a7b-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), and [IMetaDataDispenserEx](../metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="89a7b-104">Diese Methode ersetzt alle \*- `CorBindTo` Funktionen im Abschnitt [Veraltete CLR-Hostingfunktionen](deprecated-clr-hosting-functions.md) .</span><span class="sxs-lookup"><span data-stu-id="89a7b-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89a7b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="89a7b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89a7b-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="89a7b-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="89a7b-107">in Die CLSID-Schnittstelle für die Co-Klasse.</span><span class="sxs-lookup"><span data-stu-id="89a7b-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="89a7b-108">in Die IID der angeforderten `rclsid` Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="89a7b-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="89a7b-109">vorgenommen Ein Zeiger auf die abgefragte Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="89a7b-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89a7b-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="89a7b-110">Return Value</span></span>  
 <span data-ttu-id="89a7b-111">Diese Methode gibt die folgenden spezifischen HRESULTs sowie HRESULT-Fehler zurück, die Methodenfehler anzeigen.</span><span class="sxs-lookup"><span data-stu-id="89a7b-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="89a7b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89a7b-112">HRESULT</span></span>|<span data-ttu-id="89a7b-113">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="89a7b-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="89a7b-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="89a7b-114">S_OK</span></span>|<span data-ttu-id="89a7b-115">Die Methode wurde erfolgreich abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="89a7b-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="89a7b-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="89a7b-116">E_POINTER</span></span>|<span data-ttu-id="89a7b-117">`ppUnk` ist NULL.</span><span class="sxs-lookup"><span data-stu-id="89a7b-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="89a7b-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="89a7b-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="89a7b-119">Es ist nicht genügend Arbeitsspeicher verfügbar, um die Anforderung zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="89a7b-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="89a7b-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="89a7b-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="89a7b-121">Eine andere Laufzeit wurde bereits an die Legacy-Aktivierungs Richtlinie der CLR-Version 2 gebunden.</span><span class="sxs-lookup"><span data-stu-id="89a7b-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89a7b-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="89a7b-122">Remarks</span></span>  
 <span data-ttu-id="89a7b-123">Diese Methode bewirkt, dass die CLR geladen, aber nicht initialisiert wird.</span><span class="sxs-lookup"><span data-stu-id="89a7b-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="89a7b-124">In der folgenden Tabelle werden die unterstützten Kombinationen für `rclsid` und angezeigt `riid` .</span><span class="sxs-lookup"><span data-stu-id="89a7b-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="89a7b-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="89a7b-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="89a7b-126">IID_IMetaDataDispenser IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="89a7b-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="89a7b-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="89a7b-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="89a7b-128">IID_IMetaDataDispenser IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="89a7b-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="89a7b-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="89a7b-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="89a7b-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="89a7b-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="89a7b-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="89a7b-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="89a7b-132">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="89a7b-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="89a7b-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="89a7b-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="89a7b-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="89a7b-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="89a7b-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="89a7b-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="89a7b-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="89a7b-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="89a7b-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="89a7b-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="89a7b-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="89a7b-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89a7b-139">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="89a7b-139">Requirements</span></span>  
 <span data-ttu-id="89a7b-140">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89a7b-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89a7b-141">**Header:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="89a7b-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="89a7b-142">**Bibliothek:** Als Ressource in Mscoree. dll enthalten</span><span class="sxs-lookup"><span data-stu-id="89a7b-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89a7b-143">**.NET Framework Versionen:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89a7b-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89a7b-144">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="89a7b-144">See also</span></span>

- [<span data-ttu-id="89a7b-145">ICLRRuntimeInfo-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="89a7b-145">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="89a7b-146">Hostingschnittstellen</span><span class="sxs-lookup"><span data-stu-id="89a7b-146">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="89a7b-147">Hosting</span><span class="sxs-lookup"><span data-stu-id="89a7b-147">Hosting</span></span>](index.md)
