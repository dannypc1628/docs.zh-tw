---
title: 端點：每秒發生錯誤的可信賴傳訊工作階段數
ms.date: 03/30/2017
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
ms.openlocfilehash: f6b48ec4c37c28588dd874a5bfa94a01a2f43b0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61951238"
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a>端點：每秒發生錯誤的可信賴傳訊工作階段數
計數器名稱：每秒的可靠傳訊工作階段錯誤。  
  
## <a name="description"></a>描述  
 在此端點每秒發生的可信賴傳訊工作階段錯誤數。  
  
 這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
