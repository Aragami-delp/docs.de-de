---
title: METAHOST_CONFIG_FLAGS-Enumeration
ms.date: 03/30/2017
api_name:
- METAHOST_CONFIG_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_CONFIG_FLAGS
helpviewer_keywords:
- METAHOST_CONFIG_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 6f1e389f-ed99-4d6a-a0ba-72d7d869a01d
topic_type:
- apiref
ms.openlocfilehash: 6b37fcfc04e3ec880c67f102ec12d7f3e4b06a43
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493161"
---
# <a name="metahost_config_flags-enumeration"></a><span data-ttu-id="2ea3d-102">METAHOST_CONFIG_FLAGS-Enumeration</span><span class="sxs-lookup"><span data-stu-id="2ea3d-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="2ea3d-103">Beschreibt die möglichen Flags, die im- `pdwConfigFlags` Parameter der [ICLRMetaHostPolicy:: GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) -Methode zurückgegeben werden, und gibt das vorhanden sein und das Festlegen des- `useLegacyV2RuntimeActivationPolicy` Attributs im- [ \<startup> Element](../../configure-apps/file-schema/startup/startup-element.md) der Konfigurationsdatei an.</span><span class="sxs-lookup"><span data-stu-id="2ea3d-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ea3d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2ea3d-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="2ea3d-105">Member</span><span class="sxs-lookup"><span data-stu-id="2ea3d-105">Members</span></span>  
  
|<span data-ttu-id="2ea3d-106">Member</span><span class="sxs-lookup"><span data-stu-id="2ea3d-106">Member</span></span>|<span data-ttu-id="2ea3d-107">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2ea3d-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="2ea3d-108">Das- `useLegacyV2RuntimeActivationPolicy` Attribut war nicht im- [ \<startup> Element](../../configure-apps/file-schema/startup/startup-element.md)vorhanden.</span><span class="sxs-lookup"><span data-stu-id="2ea3d-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="2ea3d-109">Das `useLegacyV2RuntimeActivationPolicy` -Attribut war vorhanden und auf festgelegt `true` .</span><span class="sxs-lookup"><span data-stu-id="2ea3d-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="2ea3d-110">Das `useLegacyV2RuntimeActivationPolicy` -Attribut war vorhanden und auf festgelegt `false` .</span><span class="sxs-lookup"><span data-stu-id="2ea3d-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="2ea3d-111">Wenden Sie diese Maske auf den in zurückgegebenen Wert `pdwConfigFlags` an, um die für relevanten Werte zu erhalten `useLegacyV2RuntimeActivationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="2ea3d-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ea3d-112">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="2ea3d-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ea3d-113">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="2ea3d-113">Requirements</span></span>  
 <span data-ttu-id="2ea3d-114">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ea3d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ea3d-115">**Header:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="2ea3d-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="2ea3d-116">**Bibliothek:** Als Ressource in Mscoree. dll enthalten</span><span class="sxs-lookup"><span data-stu-id="2ea3d-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ea3d-117">**.NET Framework Versionen:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ea3d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ea3d-118">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="2ea3d-118">See also</span></span>

- [<span data-ttu-id="2ea3d-119">Hosten von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="2ea3d-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="2ea3d-120">GetRequestedRuntime-Methode</span><span class="sxs-lookup"><span data-stu-id="2ea3d-120">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)
- [<span data-ttu-id="2ea3d-121">\<startup>-Element</span><span class="sxs-lookup"><span data-stu-id="2ea3d-121">\<startup> Element</span></span>](../../configure-apps/file-schema/startup/startup-element.md)
