---
title: ICorDebugStepper::StepRange 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type:
- apiref
ms.openlocfilehash: 2ca4542fe42fab0b5ff54b23b9492d3906698c10
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120626"
---
# <a name="icordebugsteppersteprange-method"></a>ICorDebugStepper::StepRange 方法
使此 ICorDebugStepper 在其包含的執行緒上執行單一步驟，並在到達超出指定範圍的最後一個程式碼時傳回。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a>參數  
 `bStepIn`  
 在設定為 `true`，以逐步執行線上程內呼叫的函式。 設定為 [`false`] 以不進入函式。  
  
 `ranges`  
 在COR_DEBUG_STEP_RANGE 結構的陣列，其中每一個都會指定一個範圍。  
  
 `cRangeCount`  
 [in] `ranges` 陣列的大小。  
  
## <a name="remarks"></a>備註  
 `StepRange` 方法的運作方式類似[ICorDebugStepper：： Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)方法，不同之處在于到達給定範圍以外的程式碼之前，它不會完成。  
  
 這可能比一次逐步執行一個指令更有效率。 範圍會指定為從分檔器框架開頭開始的位移配對清單。  
  
 範圍會相對於方法的 Microsoft 中繼語言（MSIL）程式碼。 使用 `false` 呼叫[ICorDebugStepper：： SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) ，讓範圍相對於方法的原生程式碼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
