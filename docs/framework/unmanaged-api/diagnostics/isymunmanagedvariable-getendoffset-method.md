---
title: ISymUnmanagedVariable::GetEndOffset-Methode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
ms.openlocfilehash: 91117eae23d38f3bc608f3203ebe53f92516c9c9
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610495"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="47e64-102">ISymUnmanagedVariable::GetEndOffset-Methode</span><span class="sxs-lookup"><span data-stu-id="47e64-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="47e64-103">Ruft den Endoffset dieser Variablen in ihrem übergeordneten Element ab.</span><span class="sxs-lookup"><span data-stu-id="47e64-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="47e64-104">Wenn es sich um eine lokale Variable innerhalb eines Bereichs handelt, fällt der Endoffset in die für den Bereich definierten Offsets.</span><span class="sxs-lookup"><span data-stu-id="47e64-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47e64-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="47e64-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47e64-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="47e64-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="47e64-107">vorgenommen Ein Zeiger auf einen `ULONG32` , der den Endoffset empfängt.</span><span class="sxs-lookup"><span data-stu-id="47e64-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47e64-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="47e64-108">Return Value</span></span>  
 <span data-ttu-id="47e64-109">S_OK, wenn die Methode erfolgreich ist. andernfalls E_FAIL oder ein anderer Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="47e64-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47e64-110">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="47e64-110">Requirements</span></span>  
 <span data-ttu-id="47e64-111">**Header:** Corsym. idl, corsym. h</span><span class="sxs-lookup"><span data-stu-id="47e64-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47e64-112">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="47e64-112">See also</span></span>

- [<span data-ttu-id="47e64-113">ISymUnmanagedVariable-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="47e64-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="47e64-114">GetStartOffset-Methode</span><span class="sxs-lookup"><span data-stu-id="47e64-114">GetStartOffset Method</span></span>](isymunmanagedvariable-getstartoffset-method.md)
