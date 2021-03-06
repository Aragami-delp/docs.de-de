---
title: IMetaDataAssemblyEmit::SetFileProps-Methode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type:
- apiref
ms.openlocfilehash: 9990daea1b097532de53684921d3f10c520a3b1a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008065"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a>IMetaDataAssemblyEmit::SetFileProps-Methode
Ändert die angegebene `File`-Metadatenstruktur.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a>Parameter  
 `file`  
 in Das Metadatentoken, das die `File` zu ändernde Metadatenstruktur angibt.  
  
 `pbHashValue`  
 in Ein Zeiger auf die Hashdaten, die der Datei zugeordnet sind.  
  
 `cbHashValue`  
 in Die Größe von in Bytes `pbHashValue` .  
  
 `dwFileFlags`  
 in Eine bitweise Kombination von [CorFileFlags](corfileflags-enumeration.md) -Werten, die verschiedene Attribute der Datei angeben.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie zum Erstellen einer `File` Metadatenstruktur die [IMetaDataAssemblyEmit::D efinefile](imetadataassemblyemit-definefile-method.md) -Methode.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).  
  
 **Header:** Cor. h  
  
 **Bibliothek:** Wird als Ressource in Mscoree. dll verwendet.  
  
 **.NET Framework Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch

- [IMetaDataAssemblyEmit-Schnittstelle](imetadataassemblyemit-interface.md)
