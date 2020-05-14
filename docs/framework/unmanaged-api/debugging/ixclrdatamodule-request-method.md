---
title: 'Ixclrdatamodule:: Request-Methode'
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::Request Method
helpviewer.keywords:
- IXCLRDataModule::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 44ee4fc7fc2368b65f6f2fffe6ac239beddc6293
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395268"
---
# <a name="ixclrdatamodulerequest-method"></a><span data-ttu-id="aff8e-102">Ixclrdatamodule:: Request-Methode</span><span class="sxs-lookup"><span data-stu-id="aff8e-102">IXCLRDataModule::Request Method</span></span>

<span data-ttu-id="aff8e-103">Fordert an, den mit den Modul Daten angegebenen Puffer aufzufüllen.</span><span class="sxs-lookup"><span data-stu-id="aff8e-103">Requests to populate the buffer given with the module's data.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="aff8e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="aff8e-104">Syntax</span></span>

```cpp
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a><span data-ttu-id="aff8e-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="aff8e-105">Parameters</span></span>

`reqCode`\
<span data-ttu-id="aff8e-106">in Der zu sendende Anforderungstyp.</span><span class="sxs-lookup"><span data-stu-id="aff8e-106">[in] Request type to be sent.</span></span>

`inBufferSize`\
<span data-ttu-id="aff8e-107">[in] Größe des Eingabe Puffers, der eingegeben werden soll.</span><span class="sxs-lookup"><span data-stu-id="aff8e-107">[in] size of the input buffer to be passed in.</span></span>

`inBuffer`\
<span data-ttu-id="aff8e-108">[in, size_is (InBufferSize)] Puffer Zeiger für die Rohdaten, die in der Anforderung gesendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="aff8e-108">[in, size_is(inBufferSize)] Buffer pointer for the raw data to be sent in the request.</span></span>

`outBufferSize`\
<span data-ttu-id="aff8e-109">in Größe des Ausgabepuffers.</span><span class="sxs-lookup"><span data-stu-id="aff8e-109">[in] Size of the output buffer.</span></span>

`outBuffer`\
<span data-ttu-id="aff8e-110">[out, size_is (OutBufferSize)] Puffer Zeiger, der zum Speichern der Anforderungs Antwort verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="aff8e-110">[out, size_is(outBufferSize)] Buffer pointer to used to store the request response.</span></span>

## <a name="remarks"></a><span data-ttu-id="aff8e-111">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="aff8e-111">Remarks</span></span>

<span data-ttu-id="aff8e-112">Die bereitgestellte Methode ist Teil der `IXCLRDataModule` -Schnittstelle und entspricht dem 37. Slot der Tabelle der virtuellen Methode.</span><span class="sxs-lookup"><span data-stu-id="aff8e-112">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 37th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="aff8e-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="aff8e-113">Requirements</span></span>

<span data-ttu-id="aff8e-114">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aff8e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="aff8e-115">**Header:** Keine **Bibliothek:** keine **.NET Framework Versionen:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="aff8e-115">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="aff8e-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="aff8e-116">See also</span></span>

- [<span data-ttu-id="aff8e-117">Debuggen</span><span class="sxs-lookup"><span data-stu-id="aff8e-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="aff8e-118">IXCLRDataModule Interface-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="aff8e-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
