---
title: ICorDebugMergedAssemblyRecord::GetPublicKey-Methode
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: 51724aa1ee6101c50c7cdb4b6071fb458814f483
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213542"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="6e7e1-102">ICorDebugMergedAssemblyRecord::GetPublicKey-Methode</span><span class="sxs-lookup"><span data-stu-id="6e7e1-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="6e7e1-103">Ruft den öffentlichen Schlüssel der Assembly ab.</span><span class="sxs-lookup"><span data-stu-id="6e7e1-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e7e1-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6e7e1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,
   [out] ULONG32 *pcbPublicKey,
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e7e1-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="6e7e1-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="6e7e1-106">[in] Die maximale Anzahl der Bytes im `pbPublicKey`-Array.</span><span class="sxs-lookup"><span data-stu-id="6e7e1-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="6e7e1-107">[out] Ein Zeiger auf die tatsächliche Anzahl der in den `pbPublicKey`-Array geschriebenen Bytes.</span><span class="sxs-lookup"><span data-stu-id="6e7e1-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="6e7e1-108">[out] Ein Zeiger auf ein Bytearray, das den öffentlichen Schlüssel der Assembly enthält.</span><span class="sxs-lookup"><span data-stu-id="6e7e1-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e7e1-109">Hinweise</span><span class="sxs-lookup"><span data-stu-id="6e7e1-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e7e1-110">Diese Methode ist nur mit .NET Native verfügbar.</span><span class="sxs-lookup"><span data-stu-id="6e7e1-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e7e1-111">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="6e7e1-111">Requirements</span></span>  
 <span data-ttu-id="6e7e1-112">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e7e1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e7e1-113">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e7e1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e7e1-114">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e7e1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e7e1-115">**.NET Framework Versionen:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e7e1-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e7e1-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="6e7e1-116">See also</span></span>

- [<span data-ttu-id="6e7e1-117">ICorDebugMergedAssemblyRecord-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="6e7e1-117">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="6e7e1-118">Debugschnittstellen</span><span class="sxs-lookup"><span data-stu-id="6e7e1-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
