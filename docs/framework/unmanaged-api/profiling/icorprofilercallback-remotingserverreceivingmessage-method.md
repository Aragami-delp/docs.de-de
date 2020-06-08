---
title: ICorProfilerCallback::RemotingServerReceivingMessage-Methode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerReceivingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage method [.NET Framework profiling]
- RemotingServerReceivingMessage method [.NET Framework profiling]
ms.assetid: 5604d21f-e6b7-490e-b469-42122a7568e1
topic_type:
- apiref
ms.openlocfilehash: 157e6bc6cb9603fa9558ad6d39f0b086849fc7b0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499895"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="5ff14-102">ICorProfilerCallback::RemotingServerReceivingMessage-Methode</span><span class="sxs-lookup"><span data-stu-id="5ff14-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>
<span data-ttu-id="5ff14-103">Benachrichtigt den Profiler, dass der Prozess eine Remote Methodenaufruf-oder Aktivierungs Anforderung empfangen hat.</span><span class="sxs-lookup"><span data-stu-id="5ff14-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ff14-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="5ff14-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ff14-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="5ff14-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="5ff14-106">in Ein Wert, der dem Wert entspricht, der in [ICorProfilerCallback:: RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) unter den folgenden Bedingungen bereitgestellt wird:</span><span class="sxs-lookup"><span data-stu-id="5ff14-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="5ff14-107">Remoting-GUID-Cookies sind aktiv.</span><span class="sxs-lookup"><span data-stu-id="5ff14-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="5ff14-108">Der Kanal hat die Nachricht erfolgreich übertragen.</span><span class="sxs-lookup"><span data-stu-id="5ff14-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="5ff14-109">GUID-Cookies sind im Client seitigen Prozess aktiv.</span><span class="sxs-lookup"><span data-stu-id="5ff14-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="5ff14-110">Dies ermöglicht eine einfache Kopplung von Remote aufrufen und die Erstellung einer logischen Aufruf Stapel.</span><span class="sxs-lookup"><span data-stu-id="5ff14-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="5ff14-111">in Ein-Wert, `true` der ist, wenn der-Aufrufwert asynchron ist, andernfalls `false` .</span><span class="sxs-lookup"><span data-stu-id="5ff14-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ff14-112">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="5ff14-112">Remarks</span></span>  
 <span data-ttu-id="5ff14-113">Wenn die Nachrichten Anforderung asynchron ist, kann die Anforderung von einem beliebigen Thread gewartet werden.</span><span class="sxs-lookup"><span data-stu-id="5ff14-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ff14-114">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="5ff14-114">Requirements</span></span>  
 <span data-ttu-id="5ff14-115">**Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ff14-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ff14-116">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5ff14-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5ff14-117">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ff14-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ff14-118">**.NET Framework Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ff14-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ff14-119">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="5ff14-119">See also</span></span>

- [<span data-ttu-id="5ff14-120">ICorProfilerCallback-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5ff14-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
