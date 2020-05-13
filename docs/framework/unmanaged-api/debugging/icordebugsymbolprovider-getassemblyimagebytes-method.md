---
title: ICorDebugSymbolProvider::GetAssemblyImageBytes-Methode
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: a555acb9e23098b0a0f70924032771b1ae18e88e
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83376116"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="dced8-102">ICorDebugSymbolProvider::GetAssemblyImageBytes-Methode</span><span class="sxs-lookup"><span data-stu-id="dced8-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="dced8-103">Liest Daten aus einer zusammengeführten Assembly, wenn eine relative virtuelle Adresse (RVA) in der zusammengeführten Assembly angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="dced8-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dced8-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="dced8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,
   [in] ULONG32 length,
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dced8-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="dced8-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="dced8-106">[in] Eine relative virtuelle Adresse (RVA) in einer zusammengeführten Assembly.</span><span class="sxs-lookup"><span data-stu-id="dced8-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="dced8-107">Die Anzahl der Bytes, die aus der zusammengeführten Assembly gelesen. werden sollen.</span><span class="sxs-lookup"><span data-stu-id="dced8-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="dced8-108">Ein Zeiger auf die Adresse eines [icordebugmemorybuffer](icordebugmemorybuffer-interface.md) -Objekts, das Informationen über den Arbeitsspeicher Puffer mit zusammengeführten Assemblymetadaten enthält.</span><span class="sxs-lookup"><span data-stu-id="dced8-108">A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dced8-109">Hinweise</span><span class="sxs-lookup"><span data-stu-id="dced8-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dced8-110">Diese Methode ist nur mit .NET Native verfügbar.</span><span class="sxs-lookup"><span data-stu-id="dced8-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dced8-111">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="dced8-111">Requirements</span></span>  
 <span data-ttu-id="dced8-112">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dced8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dced8-113">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dced8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dced8-114">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dced8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dced8-115">**.NET Framework Versionen:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dced8-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dced8-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="dced8-116">See also</span></span>

- [<span data-ttu-id="dced8-117">ICorDebugSymbolProvider-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="dced8-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="dced8-118">Debugschnittstellen</span><span class="sxs-lookup"><span data-stu-id="dced8-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
