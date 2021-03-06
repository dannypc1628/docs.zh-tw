---
title: Windows Workflow Foundation 功能內容
ms.date: 03/30/2017
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
ms.openlocfilehash: c534575fcf70035bc728642dbb65b05db1fd4686
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345111"
---
# <a name="windows-workflow-foundation-feature-specifics"></a>Windows Workflow Foundation 功能內容

.NET Framework 4 新增一些功能來 Windows Workflow Foundation。 本文件將描述一些新功能，並且詳細說明適合使用這些功能的案例。

## <a name="messaging-activities"></a>傳訊活動

訊息活動（<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.SendReply>、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.ReceiveReply>）是用來從您的工作流程傳送和接收 WCF 訊息。 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 活動是用來形成透過 WSDL 公開的 Windows Communication Foundation （WCF）服務作業，就像標準的 WCF web 服務一樣。 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 用來取用類似于 WCF <xref:System.ServiceModel.ChannelFactory>的 web 服務;產生預先設定活動的 Workflow Foundation 也會有**加入服務參考**體驗。

### <a name="getting-started-with-messaging-activities"></a>傳訊活動使用者入門

- 在 Visual Studio 2012 中，建立 WCF 工作流程服務應用程式專案。 一組 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 將置於畫布上。

- 以滑鼠右鍵按一下專案，然後選取 [**加入服務參考**]。 指向現有的 web 服務 WSDL，然後按一下 **[確定]** 。 建立您的專案，以在工具箱中顯示產生的活動（使用 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.ReceiveReply>來執行）。

- [工作流程服務檔](../wcf/feature-details/workflow-services.md)

### <a name="messaging-activities-example-scenario"></a>傳訊活動範例案例

`BestPriceFinder` 服務會呼叫多個航空公司服務，以找出特定路線的最佳票證價格。 若要執行此案例，您必須使用訊息活動來接收價格要求、從後端服務取得價格，並以最佳價格回復價格要求。 它也會要求您使用其他現成可用的活動，來建立用來計算最佳價格的商務邏輯。

## <a name="workflowservicehost"></a>WorkflowServiceHost

<xref:System.ServiceModel.WorkflowServiceHost> 是現成的工作流程主機，可支援多個實例、設定和 WCF 訊息（雖然工作流程不需要使用訊息來主控）。 此外，它也會透過一組服務行為，與持續性、追蹤和執行個體控制項整合。 就像 WCF 的 <xref:System.ServiceModel.ServiceHost>，<xref:System.ServiceModel.WorkflowServiceHost> 可以在主控台/WinForms/WPF 應用程式或 Windows 服務中自我裝載，或是在 IIS 或 WAS 中由 web 裝載（如 service1.xamlx 檔案）。

### <a name="getting-started-with-workflow-service-host"></a>工作流程服務主機使用者入門

- 在 Visual Studio 2010 中，建立 WCF 工作流程服務應用程式專案：此專案將設定為在 web 主機環境中使用 <xref:System.ServiceModel.WorkflowServiceHost>。

- 若要裝載非傳訊工作流程，請加入會根據訊息建立執行個體的自訂 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>。

- 您可以將 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> 加入至 <xref:System.ServiceModel.WorkflowServiceHost>，然後使用 <xref:System.ServiceModel.Activities.WorkflowControlClient>，藉以控制工作流程執行個體 (例如暫停或終止)。

- 您可以在下列章節中找到 <xref:System.ServiceModel.WorkflowServiceHost> 的範例：

  - [執行](./samples/execution.md)

  - 應用程式：[擱置的實例管理](./samples/suspended-instance-management.md)

- [主控工作流程服務總覽](../wcf/feature-details/hosting-workflow-services-overview.md)

### <a name="workflowservicehost-scenario"></a>WorkflowServiceHost 案例

BestPriceFinder 服務會呼叫多個航空公司服務，以找出特定路線的最佳票證價格。 執行此案例需要您在 <xref:System.ServiceModel.WorkflowServiceHost>中裝載工作流程。 它也會使用訊息活動來接收價格要求、從後端服務中取出價格，並以最佳價格回復價格要求。

## <a name="correlation"></a>關聯

相互關聯是指下列其中一種情況：

- 群組訊息的方式。亦即，要求訊息與其回覆之間的關聯性。

- 將資料片段對應至服務執行個體的方式。

### <a name="getting-started"></a>使用者入門

- 若要開始使用相互關聯，請在 Visual Studio 中建立新的專案。 建立型別為 <xref:System.ServiceModel.Activities.CorrelationHandle> 的變數。

- 用來將訊息群組在一起之相互關聯的範例就是，將訊息群組在一起的要求-回覆相互關聯。

  - 在 <xref:System.ServiceModel.Activities.Receive> 活動上，按一下 [<xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>] 屬性，並使用上述第一個步驟中建立的 CorrelationHandle 來新增 <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>。

  - 以滑鼠右鍵按一下 <xref:System.ServiceModel.Activities.Receive>，然後按一下 [建立 SendReply]，以建立 <xref:System.ServiceModel.Activities.SendReply> 活動。 接著，將它貼入工作流程中 <xref:System.ServiceModel.Activities.Receive> 活動的後面。

- 將資料片段對應至服務執行個體的範例就是內容架構的相互關聯，它會將資料片段 (例如訂單 ID) 對應至特定工作流程執行個體。

  - 在任何傳訊活動上，按一下 `CorrelationInitializers` 屬性，然後使用您在上述步驟中建立的 <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 變數來加入 <xref:System.ServiceModel.Activities.CorrelationHandle>。 在下拉式功能表中，按兩下所需的訊息屬性 (例如 OrderID)。 接著，將 `CorrelatesWith` 屬性設定為上述使用的 <xref:System.ServiceModel.Activities.CorrelationHandle> 變數。

- [相互關聯概念檔](../wcf/feature-details/correlation.md)

### <a name="correlation-scenario"></a>相互關聯案例

訂單處理工作流程是用來處理新訂單的建立，並更新正在處理的現有訂單。 執行此案例需要您在 <xref:System.ServiceModel.WorkflowServiceHost> 中裝載工作流程，並使用訊息活動。 它也會要求根據 `orderId` 的相互關聯，以確保會對正確的工作流程進行更新。

## <a name="simplified-configuration"></a>簡化的組態

WCF 設定架構很複雜，可讓使用者有許多難以找到的功能。 在 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]中，我們著重于協助 WCF 使用者使用下列功能來設定其服務：

- 移除每項服務明確組態的需求。 如果您沒有為服務設定任何 \<服務 > 專案，而且您的服務並未以程式設計方式定義任何端點，則會自動將一組端點新增至您的服務，每個服務基底位址和服務所執行的每個合約各一個。

- 讓使用者定義 WCF 繫結和行為的預設值，以便套用至沒有明確組態的服務。

- 標準端點會定義可重複使用的預先設定端點，其中一個或多個端點屬性 (位址、繫結和合約) 具有固定的值，而且允許定義自訂屬性。

- 最後，<xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 可讓您執行 WCF 用戶端設定的集中管理，在應用程式域載入時間之後選取或變更設定的案例中很有用。

### <a name="getting-started"></a>使用者入門

- [WCF 4.0 的開發人員指南](https://docs.microsoft.com/previous-versions/dotnet/articles/ee354381(v=msdn.10))

- [組態通道處理站](xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601)

- [標準端點元素](xref:System.ServiceModel.Configuration.StandardEndpointElement)

- [.NET Framework 4 中的服務設定改良功能](https://blogs.msdn.microsoft.com/endpoint/2009/06/30/service-configuration-improvements-in-net-4/)

- [.NET 4 中常見的使用者錯誤： WF/WCF 服務設定名稱不鍵入](https://blogs.msdn.microsoft.com/endpoint/2009/11/09/common-user-mistake-in-net-4-mistyping-the-wfwcf-service-configuration-name/)

### <a name="simplified-configuration-scenarios"></a>簡化的組態案例

- 有經驗的 .ASMX 開發人員想要開始使用 WCF。 不過，WCF 似乎太複雜了！ 我需要在組態檔中寫入哪些資訊？ 在 .NET 4 中，您甚至可以決定完全不使用組態檔。

- 現有的 WCF 服務集非常難以設定和維護。 組態檔具有數千行 XML 程式碼，任意修改可能會非常危險。 因此需要相關協助，以便將程式碼數量減少至較容易管理的數量。

## <a name="data-contract-resolver"></a>資料合約解析程式

在 .NET 3.5 中，已知型別的設計具有一些限制：

- 您無法在序列化或還原序列化期間，以動態方式加入已知型別。

- 序列化程式無法處理不明的 xsi:type 資訊。

- 使用者無法指定想要顯示在 Wire 上的 xsi:type，以便降低 Wire 上序列化執行個體的大小。

[DataContractResolver](../wcf/samples/datacontractresolver.md)解決了 .net 4.5 中的這些問題。

### <a name="getting-started"></a>使用者入門

- [資料合約解析程式 API 檔](xref:System.Runtime.Serialization.DataContractResolver)

- [資料合約解析程式簡介](https://blogs.msdn.microsoft.com/youssefm/2009/06/05/configuring-known-types-dynamically-introducing-the-datacontractresolver/)

- 範例：

  - [DataContractResolver](../wcf/samples/datacontractresolver.md)

  - [KnownAssemblyAttribute](../wcf/samples/knownassemblyattribute.md)

### <a name="data-contract-resolver-scenarios"></a>資料合約解析程式案例

- 避免在服務中宣告數十個 <xref:System.Runtime.Serialization.KnownTypeAttribute> 物件。

- 減少 XML BLOB 的大小。

## <a name="flowchart"></a>流程圖

流程圖是已知的開發架構，可以視覺化方式表示網域問題。 它是我們在 .NET 4 中導入的新控制流程樣式。 流程圖的核心特性在於，一次只能執行一項活動。 流程圖可以表達迴圈和替代的結果，但本身無法表示同時執行的多個節點。

### <a name="getting-started"></a>使用者入門

- 在 Visual Studio 2012 中，建立工作流程主控台應用程式。 在工作流程設計工具中加入流程圖。

- 流程圖功能會使用下列類別：

  - <xref:System.Activities.Statements.Flowchart>

  - <xref:System.Activities.Statements.FlowNode>

  - <xref:System.Activities.Statements.FlowDecision>

  - <xref:System.Activities.Statements.FlowStep>

  - <xref:System.Activities.Statements.FlowSwitch%601>

- 範例：

  - [使用 TryCatch 錯誤處理流程圖活動](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

  - [招聘程序](./samples/hiring-process.md)

- 設計工具文件：

  - [Flowchart 活動設計工具](/visualstudio/workflow-designer/flowchart-activity-designers)

### <a name="flowchart-scenarios"></a>流程圖案例

流程圖活動可用來實作猜測遊戲。 猜測遊戲非常簡單：電腦會選取一個隨機數字，而玩家必須猜測該數字。 當玩家送出每項猜測時，電腦會向他顯示一個提示（也就是「試試看較小的數位」）。 如果玩家在 7 次內猜到數字，電腦會對使用者顯示特別的恭賀畫面。 您可以透過組合下列程序性活動來實作此遊戲：

- <xref:System.Activities.Statements.Sequence>

- <xref:System.Activities.Statements.While>

- <xref:System.Activities.Statements.Switch%601>

- <xref:System.Activities.Statements.TryCatch>

- <xref:System.Activities.Statements.Assign%601>

- <xref:System.Activities.Statements.If>

## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a>程序性活動 (Sequence、If、ForEach、Switch、Assign、DoWhile 和 While)

程序性活動會使用程式設計人員所熟悉的概念來提供模型循序控制流程的機制。 這些活動會啟用傳統結構化的程式設計語言結構，並在適當的情況下，提供與C#一般程式語言（如和 Visual Basic）的語言同位。

### <a name="getting-started"></a>使用者入門

- 在 Visual Studio 2012 中，建立工作流程主控台應用程式。 在工作流程設計工具中加入程序性活動。

- 範例：

  - [招聘程序](./samples/hiring-process.md)

  - [公司購買程序](./samples/corporate-purchase-process.md)

- 設計工具文件：

  - [Parallel 活動設計工具](/visualstudio/workflow-designer/parallel-activity-designer)

  - [ParallelForEach\<T > 活動設計工具](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)

### <a name="procedural-activity-scenarios"></a>程序性活動案例

- <xref:System.Activities.Statements.Parallel>：內部網路檔管理系統有檔核准工作流程。 文件必須先由數個部門的人員核准，然後才能發行至內部網路。 沒有已建立的核准順序。當檔處於「待核准」階段時，可以隨時執行這些工作。 當使用者送出文件以供檢閱時，其直屬經理、內部網路管理員和內部通訊經理就必須核准該份文件。

- <xref:System.Activities.Statements.ParallelForEach%601>：WF 應用程式可管理大型公司內部的企業採購。 企業規則表示，規劃任何採購作業之前，需要三家不同廠商的估價。 採購部門的員工會從公司的廠商清單中選取三家廠商。 選取並通知這些廠商之後，公司將等候其經濟提案。 這些提案可以按照任何順序提出。 為了在 WF 中實作此案例，我們使用了 <xref:System.Activities.Statements.ParallelForEach%601>，以便逐一查看廠商的集合並且要求其經濟提案。 蒐集所有供應項目之後，系統會選取並顯示最佳提案。

## <a name="invokemethod"></a>InvokeMethod

<xref:System.Activities.Statements.InvokeMethod> 活動允許叫用範圍內物件或型別的公用方法。 它支援叫用包含或不包含參數 (包括參數陣列) 的執行個體和靜態方法，以及泛型方法。 此外，它也允許以同步和非同步方式執行方法。

### <a name="getting-started"></a>使用者入門

- 在 Visual Studio 2012 中，建立工作流程主控台應用程式。 在工作流程設計工具中加入 <xref:System.Activities.Statements.InvokeMethod> 活動，並且針對此活動設定靜態和執行個體方法。

- 設計工具檔： [InvokeMethod 活動設計](/visualstudio/workflow-designer/invokemethod-activity-designer)工具

### <a name="invokemethod-scenarios"></a>InvokeMethod 案例

- 需要叫用範圍內物件的方法。 例如，需要將某個值加入至字典。 此時，系統會叫用字典執行個體的 Add 方法，並且提供索引鍵和值。

- 需要針對舊版 CLR 物件叫用方法。 您可以使用 <xref:System.Activities.Statements.InvokeMethod>，而非建立自訂活動來包裝該舊版類別的呼叫 (如果它在工作流程執行期間位於範圍內的話)。

## <a name="error-handling-activities"></a>錯誤處理活動

<xref:System.Activities.Statements.TryCatch> 活動提供一種機制，可攔截執行一組包含的活動期間發生的例外狀況（類似于和 Visual Basic 中C#的 Try/Catch 結構）。 <xref:System.Activities.Statements.TryCatch> 提供工作流程層級的例外狀況處理。 當系統擲回未處理的例外狀況時，就會中止工作流程，而且不會執行 Finally 區塊。 這種行為與 C# 一致。

### <a name="getting-started"></a>使用者入門

- 在 Visual Studio 2012 中，建立工作流程主控台應用程式。 在工作流程設計工具中加入 <xref:System.Activities.Statements.TryCatch> 活動。

- 範例：[使用 TryCatch 在流程圖活動中處理錯誤](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

- 設計工具檔：[錯誤處理活動設計](/visualstudio/workflow-designer/error-handling-activity-designers)工具

### <a name="error-handling-scenarios"></a>錯誤處理案例

需要執行一組活動，而且需要在發生錯誤時執行特定邏輯。 如果在錯誤處理邏輯期間發現錯誤無法復原，就會重新擲回例外狀況，而且父活動 (或主機) 將會處理此問題。

## <a name="pick-activity"></a>Pick 活動

<xref:System.Activities.Statements.Pick> 活動會提供 WF 中以事件為主的控制流程模型。 <xref:System.Activities.Statements.Pick> 包含許多分支，每個分支會先等待特定事件發生後，再開始執行。 在此設定中，<xref:System.Activities.Statements.Pick> 的行為與 <xref:System.Activities.Statements.Switch%601> 很相似，因為此活動只會執行它所接聽的其中一個事件集。 每個分支都是由事件驅動，而發生的事件會先執行對應的分支。 所有其他的分支都會取消並停止接聽事件。

### <a name="getting-started"></a>使用者入門

- 在 Visual Studio 2012 中，建立工作流程主控台應用程式。 在工作流程設計工具中加入 <xref:System.Activities.Statements.Pick> 活動。

- 範例：[使用 Pick 活動](./samples/using-the-pick-activity.md)

- 設計工具檔： [Pick 活動設計](/visualstudio/workflow-designer/pick-activity-designer)工具

### <a name="pick-scenario"></a>Pick 案例

系統需要提示使用者輸入。 在一般情況下，開發人員會使用 <xref:System.Console.ReadLine%2A> 之類的方法呼叫來提示使用者輸入。 這種設定的問題在於，直到使用者輸入某些內容為止，程式都會處於等候狀態。 在此案例中，您需要使用逾時將封鎖的活動解除封鎖。 常見的案例就是要求在指定的一段時間內完成工作。 讓封鎖的活動逾時則為 Pick 發揮功能的案例。

## <a name="wcf-routing-service"></a>WCF 路由服務

路由服務是設計成一般軟體路由器，可讓您控制 WCF 訊息在用戶端和服務之間的流動方式。 路由服務可讓您將用戶端與服務分離，讓您可以支援的設定，以及您在考慮如何裝載服務時所擁有的彈性，提供更多的自由度。 在 .NET 3.5 中，用戶端和服務已緊密結合;用戶端必須知道所需的所有服務，以及其所在位置。 此外，.NET Framework 3.5 中的 WCF 具有下列限制：

- 錯誤處理很複雜，因為此邏輯必須透過硬式編碼寫入用戶端。

- 用戶端與服務一定要使用相同的繫結。

- 很少妥善分解服務：讓用戶端與實作所有功能的單一服務通訊會比在多個服務之間選擇更簡單。

.NET 4 中的路由服務的設計，是為了讓這些問題更容易解決。 新的路由服務具有下列功能：

1. 以內容為基礎的路由 (<xref:System.ServiceModel.Dispatcher.MessageFilter> 物件會檢查訊息來判斷應該傳送的目的地)。

2. 通訊協定橋接（傳輸 & 訊息）

3. 錯誤處理 (路由器會攔截通訊例外狀況並容錯移轉至備份端點)。

4. <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> 和路由組態的動態 (記憶體中) 更新。

### <a name="getting-started"></a>使用者入門

1. 檔：[路由](../wcf/feature-details/routing.md)

2. 範例：[路由服務&#91;WCF 範例&#93; ](../wcf/samples/routing-services.md)

3. Blog：[路由規則！](https://blogs.msdn.microsoft.com/RoutingRules/)

### <a name="routing-scenarios"></a>路由案例

在下列案例中，路由服務很有用：

- 用戶端可以與多個服務通訊，而不需要直接處理所有服務。

- 用戶端可以針對用戶端要求執行其他邏輯，以便判斷要路由傳送的目的地。

- 將用戶端所執行的作業分解成多個服務實作，而不需要重構用戶端。

- 用戶端與服務可以宣告具有不同安全性設定的不同繫結。

- 用戶端可以具備更健全的功能，以防範失敗或無法使用服務的情況。

## <a name="wcf-discovery"></a>WCF 探索

WCF 探索是一種架構技術，可讓您將探索機制併入應用程式基礎結構。 您可以使用這項技術，讓服務成為可探索的服務，並且設定用戶端來搜尋服務。 用戶端不再需要對端點進行硬式編碼，讓應用程式更健全並提高容錯能力。 探索是在應用程式中建置自動組態功能的完美平台。

此產品是以 WS-Discovery 標準為建置基礎。 其設計目的是要成為可互通、可擴充且泛型的產品。 此產品支援兩種作業模式：

1. 受管理：網路上有一個了解現有服務的實體，因此用戶端會直接查詢此實體以取得資訊。 這種模式類似於 Active Directory。

2. 臨機操作：用戶端會使用多點傳送訊息來找出服務。

此外，探索訊息無從驗證網路通訊協定。您可以在支援模式需求的任何通訊協定上使用這些訊息。 例如，您可以透過 UDP 通道或任何其他支援多播訊息的網路來傳送探索多播訊息。 這些設計重點與功能彈性結合，可讓您特別針對您的解決方案調整探索。

### <a name="getting-started"></a>使用者入門

- 檔： [WCF 探索](../wcf/feature-details/wcf-discovery.md)

- 範例：[探索（範例）](../wcf/samples/discovery-samples.md)

### <a name="discovery-scenarios"></a>探索案例

開發人員不想要對端點進行硬式編碼，因為它在服務可用時處於未知狀態。 不過，開發人員想要在執行階段選擇服務。 因此，應用程式的元件之間需要降低耦合、提高健全度，以及自動組態功能。

## <a name="tracking"></a>Tracking

工作流程追蹤可讓您深入瞭解工作流程實例的執行。 追蹤事件是在工作流程實例層級，以及工作流程中的活動執行時發出。 您必須將工作流程追蹤參與者加入至工作流程主機，才能訂閱追蹤記錄。 系統會使用追蹤設定檔來篩選追蹤記錄。 .NET Framework 提供 ETW （Windows 事件追蹤）追蹤參與者，而基本設定檔則安裝在 machine.config 檔案中。

### <a name="getting-started"></a>使用者入門

1. 在 Visual Studio 2010 中，建立 WCF 工作流程服務應用程式專案。 一組 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 將置於畫布上，以便開始。

2. 開啟 web.config 並加入不含設定檔的 ETW 追蹤行為。

    1. 系統會使用預設設定檔。

    2. 開啟 [事件檢視器] 並啟用下列節點中的分析通道： [**事件檢視器**]、[**應用程式及服務記錄**檔]、[ **Microsoft**、 **Windows**、**應用程式伺服器-應用程式**]。 以滑鼠右鍵按一下 [**分析**]，然後選取 [**啟用記錄**]。

    3. 執行工作流程服務。

    4. 在事件檢視器中查看工作流程追蹤事件。

3. 範例：[追蹤](./samples/tracking.md)

4. 概念檔：[工作流程追蹤和追蹤](workflow-tracking-and-tracing.md)

## <a name="sql-workflow-instance-store"></a>SQL 工作流程執行個體存放區

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 是以 SQL Server 為基礎的執行個體存放區實作。 執行個體存放區會儲存執行中執行個體的狀態以及載入和繼續該執行個體所需的所有資料。 如果工作流程會保存，服務主機就會指示執行個體存放區儲存執行個體狀態，而且當該執行個體的訊息送達或延遲活動過期時，它就會指示執行個體存放區載入執行個體狀態。

### <a name="getting-started"></a>使用者入門

1. 在 Visual Studio 2012 中，建立包含隱含或明確 <xref:System.Activities.Statements.Persist> 活動的工作流程。 將 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 行為加入至工作流程服務主機。 您可以在程式碼或應用程式組態檔中進行這項作業。

2. 範例：[持續](/previous-versions/dotnet/netframework-4.0/dd699769(v%3dvs.100))性

3. 概念檔： [SQL 工作流程實例存放區](sql-workflow-instance-store.md)。
