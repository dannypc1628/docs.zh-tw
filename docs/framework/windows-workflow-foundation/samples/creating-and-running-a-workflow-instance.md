---
title: 建立與執行工作流程執行個體
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: d895cfa9e924ecf4d1571cf67f1c1e7069e25da5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715196"
---
# <a name="creating-and-running-a-workflow-instance"></a>建立與執行工作流程執行個體

這個範例示範如何執行工作流程執行個體。 範例中會示範如何以同步和非同步方式執行。

## <a name="demonstrates"></a>示範

<xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.

## <a name="discussion"></a>討論

範例的第一個部分會使用 <xref:System.Activities.WorkflowInvoker.Invoke%2A>。 這是執行工作流程的最基本方式。 使用 <xref:System.Activities.WorkflowInvoker.Invoke%2A> 執行的工作流程會以同步方式執行。

範例的第二部分使用 <xref:System.Activities.WorkflowApplication> 類別。 <xref:System.Activities.WorkflowApplication> 可讓您更充分掌控每一個執行個體，包括與執行中工作流程進行互動以及透過非同步方式執行工作流程的能力。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a>請參閱

- [使用 WorkflowInvoker 與 WorkflowApplication](../using-workflowinvoker-and-workflowapplication.md)
