---
title: IGCThreadControl::SuspensionStarting-Methode
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionStarting
helpviewer_keywords:
- IGCThreadControl::SuspensionStarting method [.NET Framework hosting]
- SuspensionStarting method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 0af312af-98e9-415e-b182-42e80a1aee51
topic_type:
- apiref
ms.openlocfilehash: 2acabe66e3b6b5652df20e31a9d2294c2396b54b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805103"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a>IGCThreadControl::SuspensionStarting-Methode
Benachrichtigt den Host, dass die Laufzeit eine Thread Unterbrechung für eine Garbage Collection oder eine andere Unterbrechung beginnt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a>Hinweise  
 Planen Sie keine Threads während des `SuspensionStarting` Rückrufs neu.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).  
  
 **Header:** Mscoree. h  
  
 **Bibliothek:** Als Ressource in Mscoree. dll enthalten  
  
 **.NET Framework Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen

- [IGCThreadControl-Schnittstelle](igcthreadcontrol-interface.md)
