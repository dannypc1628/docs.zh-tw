---
title: ICorProfilerInfo8::GetDynamicFunctionInfo
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 45a40d49cea2dd5f881fbd47cc2fb4bd96e8f9ff
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70243990"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a>ICorProfilerInfo8:: GetDynamicFunctionInfo 方法

抓取動態方法的相關資訊。

## <a name="syntax"></a>語法

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

#### <a name="parameters"></a>參數

`functionId` \
在要取得其資訊之函式的識別碼。

`moduleId` \
在定義函式之父類別所在模組的指標。

`ppvSig` \
脫銷函數簽章的指標。

`pbSig` \
脫銷函數簽章的位元組計數指標。

`cchName` \
[in] `wszName` 陣列的大小上限。

`pcchName` \
脫銷`wszName`陣列中的字元數。

`wszName` \
脫銷陣列`WCHAR` , 這是函式的名稱 (如果有的話)。

## <a name="remarks"></a>備註

某些方法 (例如 IL Stub 或 LCG) 沒有相關聯的中繼資料可使用[IMetaDataImport](../metadata/imetadataimport-interface.md)和[IMetaDataImport2](../metadata/imetadataimport2-interface.md) api 來抓取。 分析工具可以透過指令指標或接聽[ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md), 來遇到這類方法。

此 API 可用於抓取動態方法的相關資訊, 包括易記名稱 (如果有的話)。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** Corprof.idl .idl, Corprof.idl。h

**LIBRARY:** CorGuids.lib

**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo8 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)
