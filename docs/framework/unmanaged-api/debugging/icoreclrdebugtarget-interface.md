---
title: ICoreClrDebugTarget-Schnittstelle
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type:
- apiref
ms.openlocfilehash: c44a12ef377d29e0b33b8be86aa1d8f0aa9d26bd
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397154"
---
# <a name="icoreclrdebugtarget-interface"></a>ICoreClrDebugTarget-Schnittstelle
Stellt Methoden bereit, die Verweis Zählungen steuern, Prozesse aufzählen und den Arbeitsspeicher freigeben, der einem Debugger zugeordnet ist, der einem Remote Macintosh-Silverlight-Ziel zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a>Methoden  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[ICoreClrDebugTarget::EnumProcesses-Methode](icoreclrdebugtarget-enumprocesses-method.md)|Listet die Prozesse auf, die auf einem Remotecomputer ausgeführt werden.|  
|[ICoreClrDebugTarget::EnumRuntimes-Methode](icoreclrdebugtarget-enumruntimes-method.md)|Listet die Common Language Runtime (clrs) im angegebenen Prozess auf einem Remote Computer auf.|  
|[ICoreClrDebugTarget::FreeMemory-Methode](icoreclrdebugtarget-freememory-method.md)|Gibt den Arbeitsspeicher frei, der von den Enumerationsmethoden in dieser Klasse zugeordnet wird.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Funktion wird zurzeit nur für das Debuggen eines Silverlight-basierten Anwendungs Ziels unterstützt, das auf einem Macintosh-Remote Computer ausgeführt wird.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).  
  
 **Header:** Coreclrremotedebugginginterfaces. h  
  
 **Bibliothek:** mscordbi_macx86. dll  
  
 **.NET Framework Versionen:** 3,5 SP1  
  
## <a name="see-also"></a>Siehe auch

- [ICorDebugRemoteTarget-Schnittstelle](icordebugremotetarget-interface.md)
- [ICorDebug-Schnittstelle](icordebug-interface.md)

- [Debugschnittstellen](debugging-interfaces.md)
