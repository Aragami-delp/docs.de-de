---
title: IMetaDataImport::GetModuleRefProps-Methode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type:
- apiref
ms.openlocfilehash: f1784c9f3085ce188f9e540887dd02064f8448f3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503575"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="75759-102">IMetaDataImport::GetModuleRefProps-Methode</span><span class="sxs-lookup"><span data-stu-id="75759-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="75759-103">Ruft den Namen des Moduls ab, auf das vom angegebenen Metadatentoken verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="75759-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75759-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="75759-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,
   [in]  ULONG               cchName,
   [out] ULONG               *pchName
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75759-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="75759-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="75759-106">in Das ModuleRef-Metadatentoken, das auf das Modul verweist, um Metadateninformationen zu erhalten</span><span class="sxs-lookup"><span data-stu-id="75759-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="75759-107">vorgenommen Ein Puffer, der den Modulnamen enthalten soll.</span><span class="sxs-lookup"><span data-stu-id="75759-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="75759-108">in Die angeforderte Größe von `szName` in breit Zeichen.</span><span class="sxs-lookup"><span data-stu-id="75759-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="75759-109">vorgenommen Die zurückgegebene Größe von `szName` in breit Zeichen.</span><span class="sxs-lookup"><span data-stu-id="75759-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75759-110">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="75759-110">Requirements</span></span>  
 <span data-ttu-id="75759-111">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75759-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75759-112">**Header:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="75759-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="75759-113">**Bibliothek:** Als Ressource in Mscoree. dll enthalten</span><span class="sxs-lookup"><span data-stu-id="75759-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="75759-114">**.NET Framework Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75759-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75759-115">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="75759-115">See also</span></span>

- [<span data-ttu-id="75759-116">IMetaDataImport-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="75759-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="75759-117">IMetaDataImport2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="75759-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
