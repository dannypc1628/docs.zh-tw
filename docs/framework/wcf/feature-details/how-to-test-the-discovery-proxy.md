---
title: HOW TO：測試探索 Proxy
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 856b86241299585b80d58c6d37582463736a5935
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972909"
---
# <a name="how-to-test-the-discovery-proxy"></a>HOW TO：測試探索 Proxy
本主題是四個主題中的第四個，示範如何實作探索 Proxy。 在上一個主題中， [How to:實作使用探索 Proxy 尋找服務的用戶端應用程式](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)，實作使用探索 proxy 尋找服務，然後再呼叫服務的 WCF 用戶端應用程式。 本主題描述如何確認探索 Proxy、服務以及用戶端應用程式如預期般運作。  
  
### <a name="run-the-discovery-proxy"></a>執行探索 Proxy  
  
1. 以系統管理員身分開啟命令提示字元。  
  
2. 您可能會看到一個對話方塊顯示：Windows 防火牆已封鎖此程式的一些功能。 如果您看到此訊息，按一下**解除封鎖** 按鈕。  
  
3. 在命令提示字元內執行探索 Proxy：DiscoveryProxy.exe。  
  
4. 應用程式應該會顯示下列文字：`Proxy started. Hit Enter to exit`。  
  
### <a name="run-the-discoverable-service"></a>執行可探索的服務  
  
1. 以系統管理員身分開啟命令提示字元。  
  
2. 在命令提示字元內執行可探索的服務 Service.exe。  
  
3. DiscoveryProxy.exe 應該會顯示下列文字： `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` 。  
  
### <a name="run-the-client-application"></a>執行用戶端應用程式  
  
1. 開啟命令提示字元。  
  
2. 在命令提示字元內執行 client.exe 應用程式。  
  
3. 在幾秒之後用戶端應用程式會顯示下列文字：連接至 [服務端點]。  
  
4. 然後，service.exe 應該顯示下列文字：接收到要求的問候語，我會回應。  
  
5. 然後，client.exe 應該顯示下列文字：Hello Client ！  
  
### <a name="shut-down-the-applications"></a>關閉應用程式  
  
1. 關閉用戶端應用程式。  
  
2. 關閉服務。 探索 Proxy 會顯示下列文字：`******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`。  
  
3. 關閉探索 Proxy。  
  
## <a name="see-also"></a>另請參閱

- [WCF 探索概觀](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [如何：實作探索 Proxy](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)
- [如何：實作以探索 Proxy 註冊的可探索服務](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)
- [如何：實作使用探索 Proxy 尋找服務的用戶端應用程式](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
