---
title: CreateDebuggingInterfaceFromVersion-Funktion für Silverlight
ms.date: 03/30/2017
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
ms.openlocfilehash: f40345b09cae164660711b987f62130518736518
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208623"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="dbc8a-102">CreateDebuggingInterfaceFromVersion-Funktion für Silverlight</span><span class="sxs-lookup"><span data-stu-id="dbc8a-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>

<span data-ttu-id="dbc8a-103">Akzeptiert eine (CLR)-Versions Zeichenfolge (Common Language Runtime), die von der [Funktion "deateversionstringfrommodule](createversionstringfrommodule-function.md)" zurückgegeben wird, und gibt eine entsprechende Debuggerschnittstelle zurück (in der Regel [ICorDebug](icordebug-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="dbc8a-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbc8a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="dbc8a-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbc8a-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="dbc8a-105">Parameters</span></span>  

 `szDebuggeeVersion`\
 <span data-ttu-id="dbc8a-106">in Die Versions Zeichenfolge der CLR im Ziel-zu debuggenden Ziel, die von der [Funktion "Funktion](createversionstringfrommodule-function.md)" von "debuggende Komponente" zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="dbc8a-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`\
 <span data-ttu-id="dbc8a-107">Zeiger auf einen Zeiger auf ein COM-Objekt (`IUnknown`).</span><span class="sxs-lookup"><span data-stu-id="dbc8a-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="dbc8a-108">Dieses Objekt wird in ein [ICorDebug](icordebug-interface.md) -Objekt umgewandelt, bevor es zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="dbc8a-108">This object will be cast to an [ICorDebug](icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dbc8a-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="dbc8a-109">Return Value</span></span>

 `S_OK`\
 <span data-ttu-id="dbc8a-110">`ppCordb`verweist auf ein gültiges Objekt, das die [ICorDebug-Schnittstellen](icordebug-interface.md) Schnittstelle implementiert.</span><span class="sxs-lookup"><span data-stu-id="dbc8a-110">`ppCordb` references a valid object that implements the [ICorDebug interface](icordebug-interface.md) interface.</span></span>  
  
 `E_INVALIDARG`\
 <span data-ttu-id="dbc8a-111">Entweder `szDebuggeeVersion` oder `ppCordb` ist null.</span><span class="sxs-lookup"><span data-stu-id="dbc8a-111">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 `CORDBG_E_DEBUG_COMPONENT_MISSING`\
 <span data-ttu-id="dbc8a-112">Eine für das CLR-Debuggen erforderliche Komponente kann nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="dbc8a-112">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="dbc8a-113">Entweder " _mscordbi. dll_ " oder " _mscordaccore. dll_ " wurde nicht im gleichen Verzeichnis wie das Ziel "CoreCLR. dll" gefunden.</span><span class="sxs-lookup"><span data-stu-id="dbc8a-113">Either _mscordbi.dll_ or _mscordaccore.dll_ was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 `CORDBG_E_INCOMPATIBLE_PROTOCOL`\
 <span data-ttu-id="dbc8a-114">Entweder mscordbi.dll oder mscordaccore.dll haben nicht dieselbe Version wie die Ziel-CoreCLR.dll.</span><span class="sxs-lookup"><span data-stu-id="dbc8a-114">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="dbc8a-115">`E_FAIL`(oder andere `E_` Rückgabecodes) </span><span class="sxs-lookup"><span data-stu-id="dbc8a-115">`E_FAIL` (or other `E_` return codes)</span></span>\
 <span data-ttu-id="dbc8a-116">Eine [ICorDebug-Schnittstelle](icordebug-interface.md)kann nicht zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="dbc8a-116">Unable to return an [ICorDebug interface](icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbc8a-117">Hinweise</span><span class="sxs-lookup"><span data-stu-id="dbc8a-117">Remarks</span></span>

 <span data-ttu-id="dbc8a-118">Die zurückgegebene Schnittstelle stellt die Funktionen zum Anfügen an eine CLR in einem Zielprozess und zum Debuggen von verwaltetem Code bereit, der von der CLR ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="dbc8a-118">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbc8a-119">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="dbc8a-119">Requirements</span></span>

 <span data-ttu-id="dbc8a-120">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbc8a-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbc8a-121">**Header:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="dbc8a-121">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="dbc8a-122">**Bibliothek:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="dbc8a-122">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="dbc8a-123">**.NET Framework Versionen:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="dbc8a-123">**.NET Framework Versions:** 3.5 SP1</span></span>
