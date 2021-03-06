---
title: HOW TO：使用 Windows Forms ListView 控制項顯示資料行的子項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items
- Details view
- ListView control [Windows Forms], adding ListSubItems
- subitems
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
ms.openlocfilehash: 318521cc1377be89ef54706d80c8b2990a6ba1b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650462"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a>HOW TO：使用 Windows Forms ListView 控制項顯示資料行的子項目
Windows Form<xref:System.Windows.Forms.ListView>控制項可以顯示額外的文字或詳細資料檢視中的每個項目的子項目。 第一欄會顯示項目文字，例如員工號碼。 第二、 第三和後續的資料行中顯示第一、 第二，以及後續的相關聯的子項目。  
  
### <a name="to-add-subitems-to-a-list-item"></a>若要將子項目加入至清單項目  
  
1. 加入所需的任何資料行。 因為第一欄會顯示項目的<xref:System.Windows.Forms.ListView.Text%2A>屬性，您需要多個資料行多於可用的子項目。 如需有關如何加入資料行的詳細資訊，請參閱[How to:資料行以 Windows Form ListView 控制項中加入](how-to-add-columns-to-the-windows-forms-listview-control.md)。  
  
2. 呼叫<xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A>方法所傳回的集合<xref:System.Windows.Forms.ListViewItem.SubItems%2A>項目的屬性。 下列程式碼範例會設定 employee name 和部門的清單項目。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>另請參閱

- [ListView 控制項概觀](listview-control-overview-windows-forms.md)
- [如何：新增和移除項目，使用 Windows Forms ListView 控制項](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [如何：資料行加入 Windows Form ListView 控制項](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [如何：Windows Form ListView 控制項中顯示的圖示](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [如何：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Form)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
