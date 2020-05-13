---
title: ICorDebugType::GetStaticFieldValue-Methode
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type:
- apiref
ms.openlocfilehash: 83ac91133b226e2ac263356941c3fc3288355e7e
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379935"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a>ICorDebugType::GetStaticFieldValue-Methode
Ruft einen Schnittstellen Zeiger auf ein ICorDebugValue-Objekt ab, das den Wert des statischen Felds enthält, auf das durch das angegebene Feld Token im angegebenen Stapel Rahmen verwiesen wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Parameter  
 `fieldDef`  
 in Ein `mdFieldDef` Token, das das statische Feld angibt.  
  
 `pFrame`  
 in Ein Zeiger auf ein ICorDebug Frame-Element, das den Stapel Rahmen darstellt.  
  
 `ppValue`  
 vorgenommen Ein Zeiger auf die Adresse eines- `ICorDebugValue` Werts, der den Wert des statischen Felds enthält.  
  
## <a name="remarks"></a>Hinweise  
 Die- `GetStaticFieldValue` Methode kann nur verwendet werden, wenn der Typ ELEMENT_TYPE_CLASS oder ELEMENT_TYPE_VALUETYPE ist, wie durch die [ICorDebugType:: GetType](icordebugtype-gettype-method.md) -Methode angegeben.  
  
 Bei nicht generischen Typen ist der von ausgeführte Vorgang `GetStaticFieldValue` identisch mit dem Aufruf von [ICorDebugClass:: GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) für das ICorDebugClass-Objekt, das von [ICorDebugType:: GetClass](icordebugtype-getclass-method.md)zurückgegeben wird.  
  
 Bei generischen Typen ist ein statischer Feldwert relativ zu einer bestimmten Instanziierung. Wenn das statische Feld möglicherweise relativ zu einem Thread, einem Kontext oder einer Anwendungsdomäne sein kann, unterstützt der Stapel Rahmen den richtigen Wert für den Debugger.  
  
## <a name="remarks"></a>Hinweise  
 `GetStaticFieldValue`kann nur verwendet werden, wenn ein- `ICorDebugType::GetType` Aufrufwert den Wert ELEMENT_TYPE_CLASS oder ELEMENT_TYPE_VALUETYPE zurückgibt.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).  
  
 **Header:** CorDebug.idl, CorDebug.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
