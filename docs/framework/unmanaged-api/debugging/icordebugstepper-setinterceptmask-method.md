---
title: ICorDebugStepper::SetInterceptMask 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetInterceptMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type:
- apiref
ms.openlocfilehash: e88fa543eca39c14962f0dbbe8053829713401c8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137587"
---
# <a name="icordebugsteppersetinterceptmask-method"></a>ICorDebugStepper::SetInterceptMask 方法
設定值，指定要逐步執行的程式碼類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a>參數  
 `mask`  
 在CorDebugIntercept 列舉的值組合，指定程式碼的類型。  
  
## <a name="remarks"></a>備註  
 如果已設定攔截器的位，當遇到指定的攔截程式碼類型時，分檔器就會完成。 如果清除此位，將會略過攔截程式碼。  
  
 `SetInterceptMask` 方法可能與[ICorDebugStepper：： SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) （從使用者的觀點來看）發生未預期的互動。 例如，如果類別初始化程式碼中唯一可見的（亦即非內部）部分缺少對應資訊，而且未設定 STOP_NO_MAPPING_INFO （請參閱[ICorDebugStepper：： SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)方法和 CorDebugUnmappedStop列舉），分檔器將不會跳過類別初始化。 根據預設，只會使用 `CorDebugIntercept` 列舉的 INTERCEPT_NONE 值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
