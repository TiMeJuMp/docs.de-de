---
title: IMetaDataEmit::DefineParam-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineParam
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5abe9cf0385a42645468bf58c2f81223ac4eeead
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefineparam-method"></a>IMetaDataEmit::DefineParam-Methode
Erstellt eine Parameterdefinition mit der angegebenen Signatur für die Methode, die durch das angegebene Token verwiesen wird, und ruft ein Token für die Parameterdefinition.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT DefineParam (  
    [in]  mdMethodDef md,   
    [in]  ULONG       ulParamSeq,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,   
    [out] mdParamDef  *ppd   
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `md`  
 [in] Das Token für die Methode, deren Parameter definiert wird.  
  
 `ulParamSeq`  
 [in] Die Sequenznummer des Parameters.  
  
 `szName`  
 [in] Der Name des Parameters im Unicode-Format.  
  
 `dwParamFlags`  
 [in] Flags für den Parameter. Dies ist eine Bitmaske der `CorParamAttr` Werte.  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_`  *\**  für den konstanten Wert.  
  
 `pValue`  
 [in] Der Konstante Wert für den Parameter.  
  
 `cchValue`  
 [in] Die Größe in Unicode-Zeichen, d. h. der `pValue`.  
  
 `ppd`  
 [out] Die `mdParamDef` Token zugewiesen.  
  
## <a name="remarks"></a>Hinweise  
 Die Sequenzwerte `ulParamSeq` beginnen mit 1 für Parameter. Ein Wert zurückgegeben hat eine Sequenznummer 0.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Bibliothek:** als Ressource in MSCorEE.dll verwendet  
  
 **.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [IMetaDataEmit-Schnittstelle](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2-Schnittstelle](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)