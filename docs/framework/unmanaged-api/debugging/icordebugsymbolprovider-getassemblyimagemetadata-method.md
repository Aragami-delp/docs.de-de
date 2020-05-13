---
title: ICorDebugSymbolProvider::GetAssemblyImageMetadata-Methode
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
ms.openlocfilehash: d118f0c984663e0844783ff52859698dd5335058
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83376143"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="12f21-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata-Methode</span><span class="sxs-lookup"><span data-stu-id="12f21-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="12f21-103">Gibt die Metadaten aus einer zusammengeführten Assembly zurück.</span><span class="sxs-lookup"><span data-stu-id="12f21-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12f21-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="12f21-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12f21-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="12f21-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="12f21-106">vorgenommen Ein Zeiger auf die Adresse eines [icordebugmemorybuffer](icordebugmemorybuffer-interface.md) -Objekts, das Informationen über die Größe und die Adresse der Metadaten der zusammengeführten Assembly enthält.</span><span class="sxs-lookup"><span data-stu-id="12f21-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12f21-107">Hinweise</span><span class="sxs-lookup"><span data-stu-id="12f21-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12f21-108">Diese Methode ist nur mit .NET Native verfügbar.</span><span class="sxs-lookup"><span data-stu-id="12f21-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12f21-109">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="12f21-109">Requirements</span></span>  
 <span data-ttu-id="12f21-110">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12f21-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12f21-111">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12f21-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12f21-112">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12f21-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12f21-113">**.NET Framework Versionen:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12f21-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f21-114">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="12f21-114">See also</span></span>

- [<span data-ttu-id="12f21-115">ICorDebugSymbolProvider-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="12f21-115">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="12f21-116">Debugschnittstellen</span><span class="sxs-lookup"><span data-stu-id="12f21-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
