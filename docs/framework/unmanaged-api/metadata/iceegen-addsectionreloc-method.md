---
title: ICeeGen::AddSectionReloc 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.AddSectionReloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type:
- apiref
ms.openlocfilehash: e5940f229e86b46bb8c5d5b2f9920a8261359f65
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436417"
---
# <a name="iceegenaddsectionreloc-method"></a>ICeeGen::AddSectionReloc 方法
將 reloc 指令新增至程式碼基底。  
  
 這個方法已過時，不應使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a>參數  
 `section`  
 在要加入 reloc 指令的記憶體內部程式碼區段。  
  
 `offset`  
 在區段的位移。  
  
 `relativeTo`  
 在`offset` 所參考的區段。  
  
 `relocType`  
 在其中一個[CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md)值，表示要新增的 reloc 指令類型。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICeeGen 介面](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
