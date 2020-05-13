---
title: ICorDebugManagedCallback::Break-Methode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Break
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type:
- apiref
ms.openlocfilehash: f70a88df00d15729a6bde06b49417b6439f7c0ec
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212463"
---
# <a name="icordebugmanagedcallbackbreak-method"></a><span data-ttu-id="741a8-102">ICorDebugManagedCallback::Break-Methode</span><span class="sxs-lookup"><span data-stu-id="741a8-102">ICorDebugManagedCallback::Break Method</span></span>

<span data-ttu-id="741a8-103">Benachrichtigt den Debugger, wenn eine <xref:System.Reflection.Emit.OpCodes.Break> Anweisung im Codestream ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="741a8-103">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="741a8-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="741a8-104">Syntax</span></span>

```cpp
HRESULT Break (
    [in] ICorDebugAppDomain *pAppDomain,
    [in] ICorDebugThread    *thread
);
```

## <a name="parameters"></a><span data-ttu-id="741a8-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="741a8-105">Parameters</span></span>

`pAppDomain`\
<span data-ttu-id="741a8-106">in Ein Zeiger auf ein ICorDebugAppDomain-Objekt, das die Anwendungsdomäne darstellt, die die Break-Anweisung enthält.</span><span class="sxs-lookup"><span data-stu-id="741a8-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the break instruction.</span></span>

`thread`\
<span data-ttu-id="741a8-107">in Ein Zeiger auf ein ICorDebugThread-Objekt, das den Thread darstellt, der die Break-Anweisung enthält.</span><span class="sxs-lookup"><span data-stu-id="741a8-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the break instruction.</span></span>

## <a name="requirements"></a><span data-ttu-id="741a8-108">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="741a8-108">Requirements</span></span>

<span data-ttu-id="741a8-109">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="741a8-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="741a8-110">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="741a8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="741a8-111">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="741a8-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="741a8-112">**.NET Framework Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="741a8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="741a8-113">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="741a8-113">See also</span></span>

- [<span data-ttu-id="741a8-114">ICorDebugManagedCallback-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="741a8-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
