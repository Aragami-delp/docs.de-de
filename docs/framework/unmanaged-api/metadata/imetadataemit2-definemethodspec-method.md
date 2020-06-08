---
title: IMetaDataEmit2::DefineMethodSpec-Methode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineMethodSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineMethodSpec
helpviewer_keywords:
- DefineMethodSpec method [.NET Framework metadata]
- IMetaDataEmit2::DefineMethodSpec method [.NET Framework metadata]
ms.assetid: 3c24e552-fc69-4971-b65a-a3e4b5f7f1e8
topic_type:
- apiref
ms.openlocfilehash: 8e067dc4943e6847177c13a683703e3a649a49e4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503819"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="d549e-102">IMetaDataEmit2::DefineMethodSpec-Methode</span><span class="sxs-lookup"><span data-stu-id="d549e-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="d549e-103">Erstellt eine generische Instanz einer Methode und ruft ein Token für die Definition ab.</span><span class="sxs-lookup"><span data-stu-id="d549e-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d549e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="d549e-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d549e-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="d549e-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="d549e-106">in Ein Token für die Methode, von der die generische Instanz erstellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="d549e-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="d549e-107">Das Token muss den Typ `mdMethodDef` oder aufweisen `mdMemberRef` .</span><span class="sxs-lookup"><span data-stu-id="d549e-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="d549e-108">in Ein Zeiger auf die binäre com+-Signatur der Methode.</span><span class="sxs-lookup"><span data-stu-id="d549e-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="d549e-109">in Die Größe von in Bytes `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="d549e-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="d549e-110">vorgenommen Ein Token für die Metadatensignatur-Definition der Methode.</span><span class="sxs-lookup"><span data-stu-id="d549e-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d549e-111">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="d549e-111">Requirements</span></span>  
 <span data-ttu-id="d549e-112">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d549e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d549e-113">**Header:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d549e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d549e-114">**Bibliothek:** Wird als Ressource in Mscoree. dll verwendet.</span><span class="sxs-lookup"><span data-stu-id="d549e-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d549e-115">**.NET Framework Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d549e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d549e-116">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="d549e-116">See also</span></span>

- [<span data-ttu-id="d549e-117">IMetaDataEmit2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="d549e-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="d549e-118">IMetaDataEmit-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="d549e-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
