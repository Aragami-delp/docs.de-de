---
title: IMetaDataEmit::DeletePinvokeMap-Methode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeletePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeletePinvokeMap
helpviewer_keywords:
- IMetaDataEmit::DeletePinvokeMap method [.NET Framework metadata]
- DeletePinvokeMap method [.NET Framework metadata]
ms.assetid: 3c4f6b54-5ce7-4a2a-83e1-6dec16441f50
topic_type:
- apiref
ms.openlocfilehash: 79af7b5679598ffa82471dcb69adabc2394b13fa
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009300"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="a4c08-102">IMetaDataEmit::DeletePinvokeMap-Methode</span><span class="sxs-lookup"><span data-stu-id="a4c08-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="a4c08-103">Zerstört die PInvoke-Zuordnungsmetadaten für das Objekt, auf das durch das angegebene Token verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="a4c08-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4c08-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a4c08-104">Syntax</span></span>  
  
```cpp  
HRESULT DeletePinvokeMap (
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4c08-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="a4c08-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a4c08-106">in Ein- `mdFieldDef` oder- `mdMethodDef` Token, das das Objekt darstellt, für das die PInvoke-Mapping-Metadaten gelöscht werden sollen.</span><span class="sxs-lookup"><span data-stu-id="a4c08-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4c08-107">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="a4c08-107">Requirements</span></span>  
 <span data-ttu-id="a4c08-108">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4c08-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4c08-109">**Header:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a4c08-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a4c08-110">**Bibliothek:** Wird als Ressource in Mscoree. dll verwendet.</span><span class="sxs-lookup"><span data-stu-id="a4c08-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4c08-111">**.NET Framework Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4c08-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c08-112">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a4c08-112">See also</span></span>

- [<span data-ttu-id="a4c08-113">IMetaDataEmit-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="a4c08-113">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="a4c08-114">IMetaDataEmit2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="a4c08-114">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
