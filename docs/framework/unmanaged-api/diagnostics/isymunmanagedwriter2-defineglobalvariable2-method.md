---
title: ISymUnmanagedWriter2::DefineGlobalVariable2-Methode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineGlobalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2 method [.NET Framework debugging]
- DefineGlobalVariable2 method [.NET Framework debugging]
ms.assetid: 04d569d6-a151-4957-9872-f3f694c3e4a9
topic_type:
- apiref
ms.openlocfilehash: ed3c841c34b71b30f740117899353aa289e478d5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614707"
---
# <a name="isymunmanagedwriter2defineglobalvariable2-method"></a><span data-ttu-id="8399d-102">ISymUnmanagedWriter2::DefineGlobalVariable2-Methode</span><span class="sxs-lookup"><span data-stu-id="8399d-102">ISymUnmanagedWriter2::DefineGlobalVariable2 Method</span></span>
<span data-ttu-id="8399d-103">Definiert eine einzelne globale Variable.</span><span class="sxs-lookup"><span data-stu-id="8399d-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8399d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="8399d-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineGlobalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8399d-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="8399d-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="8399d-106">in Der Name der globalen Variablen.</span><span class="sxs-lookup"><span data-stu-id="8399d-106">[in] The global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="8399d-107">in Die globalen Variablen Attribute.</span><span class="sxs-lookup"><span data-stu-id="8399d-107">[in] The global variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="8399d-108">in Das Metadatentoken der Signatur.</span><span class="sxs-lookup"><span data-stu-id="8399d-108">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="8399d-109">in Der adrestyp.</span><span class="sxs-lookup"><span data-stu-id="8399d-109">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="8399d-110">in Die erste Adresse für die Parameter Spezifikation.</span><span class="sxs-lookup"><span data-stu-id="8399d-110">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="8399d-111">in Die zweite Adresse für die Parameter Spezifikation.</span><span class="sxs-lookup"><span data-stu-id="8399d-111">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="8399d-112">in Die dritte Adresse für die Parameter Spezifikation.</span><span class="sxs-lookup"><span data-stu-id="8399d-112">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8399d-113">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="8399d-113">Return Value</span></span>  
 <span data-ttu-id="8399d-114">S_OK, wenn die Methode erfolgreich ist. andernfalls E_FAIL oder ein anderer Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="8399d-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8399d-115">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="8399d-115">Requirements</span></span>  
 <span data-ttu-id="8399d-116">**Header:** Corsym. idl</span><span class="sxs-lookup"><span data-stu-id="8399d-116">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8399d-117">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8399d-117">See also</span></span>

- [<span data-ttu-id="8399d-118">ISymUnmanagedWriter2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="8399d-118">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="8399d-119">DefineGlobalVariable-Methode</span><span class="sxs-lookup"><span data-stu-id="8399d-119">DefineGlobalVariable Method</span></span>](isymunmanagedwriter-defineglobalvariable-method.md)
