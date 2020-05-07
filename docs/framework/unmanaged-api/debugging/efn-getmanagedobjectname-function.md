---
title: _EFN_GetManagedObjectName-Funktion
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectName
helpviewer_keywords:
- _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type:
- apiref
ms.openlocfilehash: 708ac2e407bf6f87dbe314a0e87cdd16f45b2bcf
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860753"
---
# <a name="_efn_getmanagedobjectname-function"></a>\_EFN\_getmanagedobjectname-Funktion
Ruft den Namen eines Typs mithilfe des bereitgestellten verwalteten Objekt Zeigers ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a>Parameter  
 `Client`  
 in Ein Zeiger auf den Debugclient.  
  
 `objAddr`  
 in Ein Zeiger für verwaltete Objekte.  
  
 szName  
 vorgenommen Der Name des Typs.  
  
 `cbName`  
 vorgenommen Die Anzahl von Zeichen, die im Zeichen folgen Puffer verfügbar sind.  
  
## <a name="remarks"></a>Hinweise  
 Wenn im Thread derzeit kein verwalteter Code vorhanden ist, gibt die Funktion HRESULT SOS_E_NOMANAGEDCODE mit einem Einrichtungs Wert von 0xa0 und dem Fehlercode 0x1000 zurück.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).  
  
 **Header:** SOS_Stacktrace. h  
  
 **.NET Framework Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen:

- [Debuggen von globalen statischen Funktionen](debugging-global-static-functions.md)
