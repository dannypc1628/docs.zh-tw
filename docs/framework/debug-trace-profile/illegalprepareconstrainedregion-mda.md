---
title: illegalPrepareConstrainedRegion MDA
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 623aff91eb801b4b32fc180bd97ed3822ad7f163
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052679"
---
# <a name="illegalprepareconstrainedregion-mda"></a>illegalPrepareConstrainedRegion MDA
<xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> 方法呼叫並未緊接在例外狀況處理常式的 `try` 陳述式前面時，`illegalPrepareConstrainedRegion` Managed 偵錯助理 (MDA) 就會啟動。 這項限制屬於 MSIL 層級，因此可允許在呼叫和 `try` 之間具有不產生程式碼的來源，例如註解。  
  
## <a name="symptoms"></a>徵兆  
 限制的執行區域 (CER) 永遠不會被視為這類執行區執，而是當成簡單的例外狀況處理區塊 (`finally` 或`catch`)。 因此，這個區域不會在發生記憶體不足狀況或執行緒中止的情況下執行。  
  
## <a name="cause"></a>原因  
 未正確地遵循 CER 的準備模式。  這是一個錯誤事件。 用<xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>來標記例外狀況處理常式的方法呼叫，在其`fault` `catch` `finally` / / / 區塊中引進CER時，必須緊接`filter`在`try`語句。  
  
## <a name="resolution"></a>解決方式  
 請確定對 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 的呼叫緊接在 `try` 陳述式前面。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 此 MDA 對 CLR 沒有影響。  
  
## <a name="output"></a>Output  
 MDA 會顯示呼叫 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 方法的方法名稱、MSIL 位移，以及指出呼叫並未緊接在 try 區塊開頭前面的訊息。  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>範例  
 下列程式碼範例示範會導致此 MDA 啟動的模式。  
  
```csharp
void MethodWithInvalidPCR()  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    Object o = new Object();  
    try  
    {  
        …  
    }  
    finally  
    {  
        …  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [診斷 Managed 偵錯助理的錯誤](diagnosing-errors-with-managed-debugging-assistants.md)
- [Interop 封送處理](../interop/interop-marshaling.md)
