---
title: IMetaDataImport::FindTypeRef-Methode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type:
- apiref
ms.openlocfilehash: 545fe1e1d9e641d2225ad92c11453558dc4b97d1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491497"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="6b677-102">IMetaDataImport::FindTypeRef-Methode</span><span class="sxs-lookup"><span data-stu-id="6b677-102">IMetaDataImport::FindTypeRef Method</span></span>
<span data-ttu-id="6b677-103">Ruft einen Zeiger auf das TypeRef-Token für den <xref:System.Type> Verweis ab, der sich im angegebenen Bereich befindet und den angegebenen Namen aufweist.</span><span class="sxs-lookup"><span data-stu-id="6b677-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b677-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6b677-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b677-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="6b677-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="6b677-106">in Ein ModuleRef-, AssemblyRef-oder TypeRef-Token, das bzw. die das Modul, die Assembly oder den Typ angibt, in dem der Typverweis definiert ist.</span><span class="sxs-lookup"><span data-stu-id="6b677-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="6b677-107">in Der Name des Typverweises, nach dem gesucht werden soll.</span><span class="sxs-lookup"><span data-stu-id="6b677-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="6b677-108">vorgenommen Ein Zeiger auf das übereinstimmende TypeRef-Token.</span><span class="sxs-lookup"><span data-stu-id="6b677-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b677-109">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="6b677-109">Requirements</span></span>  
 <span data-ttu-id="6b677-110">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b677-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b677-111">**Header:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6b677-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6b677-112">**Bibliothek:** Als Ressource in Mscoree. dll enthalten</span><span class="sxs-lookup"><span data-stu-id="6b677-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6b677-113">**.NET Framework Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b677-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b677-114">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="6b677-114">See also</span></span>

- [<span data-ttu-id="6b677-115">IMetaDataImport-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="6b677-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="6b677-116">IMetaDataImport2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="6b677-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
