---
title: ICorProfilerInfo::GetCodeInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCodeInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type:
- apiref
ms.openlocfilehash: 2393468f78312511d11cbe0ab422c26c710e25d8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439235"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a>ICorProfilerInfo::GetCodeInfo 方法
取得與指定函式識別碼相關聯的機器碼範圍。  
  
 這個方法已過時。 請改用[ICorProfilerInfo2：： GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a>參數  
 `functionId`  
 [in] 與機器碼關聯的函式識別碼。  
  
 `pStart`  
 [out] 構成函式機器碼的位元組陣列指標。  
  
 `pcSize`  
 [out] 整數的指標，此整數指定機器碼的大小，以位元組為單位。  
  
## <a name="remarks"></a>備註  
 為了最佳化效能，.NET Framework 2.0 版中的執行階段會將先行編譯的函式機器碼分割成多個區域。 因此，`GetCodeInfo` 方法在 .NET Framework 2.0 中已過時，因為它無法處理函式機器碼的範圍。 分析工具應改為使用較為通用的 `ICorProfilerInfo2::GetCodeInfo2` 方法。  
  
 這個函式會使用呼叫端配置的緩衝區。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 1.0  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
