---
title: HOW TO：處理 Windows Forms DataGridView 控制項在資料輸入期間發生的錯誤
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
ms.assetid: 9004e72f-fdec-4264-a37d-2c99764efc13
ms.openlocfilehash: 6297eaea93caea5d19af9740d2b5a1066507ff15
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592067"
---
# <a name="how-to-handle-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>HOW TO：處理 Windows Forms DataGridView 控制項在資料輸入期間發生的錯誤
下列程式碼範例示範如何使用 <xref:System.Windows.Forms.DataGridView> 控制項，將資料輸入錯誤回報給使用者。  
  
 如需這個程式碼範例的完整說明，請參閱[逐步解說：處理在 Windows 中的資料輸入期間所發生的錯誤 Form DataGridView 控制項](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#00)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- System、System.Data、System.Windows.Forms 和 System.XML 組件的參考。   
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](../../data/adonet/protecting-connection-information.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [逐步解說：處理 Windows Form DataGridView 控制項中的資料輸入期間所發生的錯誤](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Windows Forms DataGridView 控制項中的資料輸入](data-entry-in-the-windows-forms-datagridview-control.md)
- [逐步解說：驗證 Windows Form DataGridView 控制項中的資料](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [保護連線資訊](../../data/adonet/protecting-connection-information.md)
