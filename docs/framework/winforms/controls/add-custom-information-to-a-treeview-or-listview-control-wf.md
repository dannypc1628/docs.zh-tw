---
title: 作法：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- ListItem
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- examples [Windows Forms], ListView control
- ListView control [Windows Forms], adding custom information
- TreeView control [Windows Forms], adding custom information
ms.assetid: 68be11de-1d5b-430e-901f-cfbe48d14b19
ms.openlocfilehash: f588a00c430eb1ae1f0cdcde6b7dd22f0c8671c5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956991"
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a>作法：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)
您可以在<xref:System.Windows.Forms.TreeView> <xref:System.Windows.Forms.ListView>控制項中的 Windows Forms 控制項或衍生專案中建立衍生節點。 衍生可讓您新增您所需的任何欄位，以及新增自訂方法和建構函式來處理它們。 這項功能的其中一個用途是將 Customer 物件附加至每個樹狀節點或清單項目。 這裡的範例適用于<xref:System.Windows.Forms.TreeView>控制項, 但相同的方法也可<xref:System.Windows.Forms.ListView>用於控制項。  
  
### <a name="to-derive-a-tree-node"></a>衍生樹狀節點  
  
- 建立新的節點類別 (衍生<xref:System.Windows.Forms.TreeNode>自類別), 其中包含用來記錄檔案路徑的自訂欄位。  
  
    ```vb  
    Class myTreeNode  
       Inherits TreeNode  
  
       Public FilePath As String  
  
       Sub New(ByVal fp As String)  
          MyBase.New()  
          FilePath = fp  
          Me.Text = fp.Substring(fp.LastIndexOf("\"))  
       End Sub  
    End Class  
    ```  
  
    ```csharp  
    class myTreeNode : TreeNode  
    {  
       public string FilePath;  
  
       public myTreeNode(string fp)  
       {  
          FilePath = fp;  
          this.Text = fp.Substring(fp.LastIndexOf("\\"));  
       }  
    }  
    ```  
  
    ```cpp  
    ref class myTreeNode : public TreeNode  
    {  
    public:  
       System::String ^ FilePath;  
  
       myTreeNode(System::String ^ fp)  
       {  
          FilePath = fp;  
          this->Text = fp->Substring(fp->LastIndexOf("\\"));  
       }  
    };  
    ```  
  
### <a name="to-use-a-derived-tree-node"></a>使用衍生樹狀節點  
  
1. 您可以使用新的衍生樹狀節點做為函式呼叫的參數。  
  
     在下列範例中，針對文字檔案位置設定的路徑是 [我的文件] 資料夾。 這是因為您可以假設大部分執行 Windows 作業系統的電腦都會包含這個目錄。 也可讓具備最小系統存取層級的使用者安全地執行應用程式。  
  
    ```vb  
    ' You should replace the bold text file   
    ' in the sample below with a text file of your own choosing.  
    TreeView1.Nodes.Add(New myTreeNode (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\ TextFile.txt ") )  
    ```  
  
    ```csharp  
    // You should replace the bold text file   
    // in the sample below with a text file of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    treeView1.Nodes.Add(new myTreeNode(System.Environment.GetFolderPath
       (System.Environment.SpecialFolder.Personal)
       + @"\TextFile.txt") );  
    ```  
  
    ```cpp  
    // You should replace the bold text file   
    // in the sample below with a text file of your own choosing.  
    treeView1->Nodes->Add(new myTreeNode(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\TextFile.txt")));  
    ```  
  
2. 如果您傳遞樹狀節點, 而且它是以<xref:System.Windows.Forms.TreeNode>類別的形式輸入, 則您必須將轉換成衍生類別。 轉型是物件類型之間的明確轉換。 如需轉換的詳細資訊, 請參閱[隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)(Visual Basic)、轉[型和類型轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)(Visual C#) 或[Cast 運算子: ()](/cpp/cpp/cast-operator-parens) (visual C++)。  
  
    ```vb  
    Public Sub TreeView1_AfterSelect(ByVal sender As Object, ByVal e As System.Windows.Forms.TreeViewEventArgs) Handles TreeView1.AfterSelect  
       Dim mynode As myTreeNode  
       mynode = CType(e.node, myTreeNode)  
       MessageBox.Show("Node selected is " & mynode.filepath)  
    End Sub  
    ```  
  
    ```csharp  
    protected void treeView1_AfterSelect (object sender,  
    System.Windows.Forms.TreeViewEventArgs e)  
    {  
       myTreeNode myNode = (myTreeNode)e.Node;  
       MessageBox.Show("Node selected is " + myNode.FilePath);  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void treeView1_AfterSelect(System::Object ^  sender,  
          System::Windows::Forms::TreeViewEventArgs ^  e)  
       {  
          myTreeNode ^ myNode = safe_cast<myTreeNode^>(e->Node);  
          MessageBox::Show(String::Concat("Node selected is ",   
             myNode->FilePath));  
       }  
    ```  
  
## <a name="see-also"></a>另請參閱

- [TreeView 控制項](treeview-control-windows-forms.md)
- [ListView 控制項](listview-control-windows-forms.md)
