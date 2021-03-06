---
title: CALL_ID 結構
ms.date: 03/30/2017
api_name:
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
ms.openlocfilehash: 8c606f67766334800444f39b115d90f65ecca13d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448590"
---
# <a name="call_id-structure"></a>CALL_ID 結構
提供有關所呼叫函式之偵錯工具的資訊。 如需詳細資訊，請參閱[INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)介面。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`szMachine`|識別正在進行呼叫的電腦。|  
|`dwPid`|識別機器處理器。|  
|`pUserThread`|識別正在執行呼叫的執行緒。|  
|`addrStackPointer`|指定呼叫堆疊的位址。|  
|`szEntryPoint`|指定呼叫的位址。|  
|`szDestinationMachine`|識別將執行呼叫的電腦。|  
  
## <a name="requirements"></a>需求  
 **標頭：** ProtocolNotify2 .idl  
  
## <a name="see-also"></a>另請參閱

- [INotifySink2 介面](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [診斷符號存放區結構](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
