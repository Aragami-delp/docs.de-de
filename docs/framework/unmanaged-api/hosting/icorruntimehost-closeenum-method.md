---
title: ICorRuntimeHost::CloseEnum-Methode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CloseEnum
helpviewer_keywords:
- CloseEnum method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::CloseEnum method [.NET Framework hosting]
ms.assetid: f7ce7e8c-0a3e-4587-a180-063e2b85940e
topic_type:
- apiref
ms.openlocfilehash: a5a86df3ac1f50ca624490ad80a6fed903433436
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762369"
---
# <a name="icorruntimehostcloseenum-method"></a>ICorRuntimeHost::CloseEnum-Methode
Setzt einen Domänen Enumerator auf den Anfang der Domänen Liste zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a>Parameter  
 `hEnum`  
 in Der zurück zusetzenden Enumerator.  
  
## <a name="return-value"></a>Rückgabewert  
  
|HRESULT|BESCHREIBUNG|  
|-------------|-----------------|  
|S_OK|Der Vorgang wurde durchgeführt.|  
|S_FALSE|Der Vorgang konnte nicht ausgeführt werden.|  
|E_FAIL|Ein unbekannter, schwerwiegender Fehler ist aufgetreten. Wenn eine Methode E_FAIL zurückgibt, ist die Common Language Runtime (CLR) im Prozess nicht mehr verwendbar. Nachfolgende Aufrufe von Hosting-APIs geben HOST_E_CLRNOTAVAILABLE zurück.|  
|HOST_E_CLRNOTAVAILABLE|Die CLR wurde nicht in einen Prozess geladen, oder die CLR befindet sich in einem Zustand, in dem Sie verwalteten Code nicht ausführen oder den-Befehl nicht erfolgreich verarbeiten kann.|  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).  
  
 **Header:** Mscoree. h  
  
 **Bibliothek:** Als Ressource in Mscoree. dll enthalten  
  
 **.NET Framework Versionen:** 1,0, 1,1  
  
## <a name="see-also"></a>Weitere Informationen

- [CorBindToRuntimeEx-Funktion](corbindtoruntimeex-function.md)
- [ICorRuntimeHost-Schnittstelle](icorruntimehost-interface.md)
