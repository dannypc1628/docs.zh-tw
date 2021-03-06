---
title: 標準控制項的 UI 自動化支援
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: ed5e4f6ab23fe9ae77c94616a668da8accb46d4b
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741708"
---
# <a name="ui-automation-support-for-standard-controls"></a>標準控制項的 UI 自動化支援
> [!NOTE]
> 這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](/windows/win32/winauto/entry-uiauto-win32)。  
  
 本主題包含針對 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]、Win32 和 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] 架構所開發之應用程式中的標準控制項 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 支援的相關資訊。  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a>Windows Presentation Foundation 控制項  
 提供資訊或支援使用者互動的所有 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 控制項項目，都有 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的完整原生支援。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]看不見其他如面板等的項目。  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a>Win32 控制項  
 大部分的 Win32 控制項都會透過 Uiautomationclientsideproviders.dll 中的用戶端提供者公開給 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]。 此組件會自動註冊為用於使用者介面自動化用戶端應用程式。  
  
 僅針對第6版*ComCtrl32*的控制項提供完整支援。  
  
 支援的控制項如下。  
  
|類別名稱|控制項類型|  
|----------------|------------------|  
|按鈕|按鈕|  
|按鈕|RadioButton|  
|按鈕|群組|  
|按鈕|核取方塊|  
|按鈕|超連結|  
|按鈕|SplitButton|  
|按鈕|核取方塊|  
|ComboBoxEx32|ComboBox|  
|ComboBox|ComboBox|  
|Edit|文件|  
|Edit|Edit|  
|SysLink|超連結|  
|Static|文字|  
|Static|Image|  
|SysIPAddress32|自訂|  
|SysHeader32|Header/HeaderItem|  
|SysListView32|DataGrid|  
|SysListView32|清單|  
|ListBox|清單|  
|ListBox|ListItem|  
|#32768|功能表|  
|#32768|MenuItem|  
|msctls_progress32|ProgressBar|  
|RichEdit|Document. 請參閱「注意」。|  
|RichEdit20A|文件|  
|RichEdit20W|文件|  
|RichEdit50W|文件|  
|ScrollBar|滑桿|  
|msctls_trackbar32|滑桿|  
|msctls_updown32|Spinner|  
|msctls_statusbar32|StatusBar|  
|SysTabControl32|索引標籤|  
|SysTabControl32|TabItem|  
|ToolbarWindow32|ToolBar|  
|ToolbarWindow32|MenuItem|  
|ToolbarWindow32|按鈕|  
|ToolbarWindow32|核取方塊|  
|ToolbarWindow32|RadioButton|  
|ToolbarWindow32|Separator|  
|tooltips_class32|ToolTip|  
|#32774|ToolTip|  
|ReBarWindow32|ToolBar|  
|SysTreeView32|樹狀結構|  
|SysTreeView32|TreeItem|  
  
 **注意**RichEdit 控制項僅支援 Windows Vista 隨附的版本（在 Riched20.dll 版本3.1 和更新版本中，以及 4.1 Msftedit.dll 和更新版本）。  
  
 不支援的控制項如下。  
  
|類別名稱|控制項類型|  
|----------------|------------------|  
|SysAnimate32|Image|  
|SysPager|Spinner|  
|SysDateTimePick32|自訂|  
|SysMonthCal32|行事曆|  
|MS_WINNOTE|ToolTip|  
|VBBubble|ToolTip|  
|ScrollBar (當做獨立控制項使用時)|滑桿|  
|SuperGrid|自訂|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a>Windows Form 控制項  
 Windows Forms 控制項會透過 Uiautomationclientsideproviders.dll 中的用戶端提供者公開給 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]。 此組件會自動註冊為用於使用者介面自動化用戶端應用程式。  
  
 一般來說，[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]支援 Windows Forms 控制項，這是 Win32 通用控制項的 managed 包裝函式。 支援的控制項如下。  
  
|類別名稱|  
|----------------|  
|按鈕|  
|核取方塊|  
|CheckedListBox|  
|ColorDialog|  
|ComboBox|  
|FolderBrowser|  
|FontDialog|  
|GroupBox|  
|HscrollBar|  
|ImageList|  
|ThisAddIn|  
|ListBox|  
|ListView|  
|MainMenu/ContextMenu|  
|MonthCalendar|  
|NotifyIcon|  
|OpenFileDialog|  
|PageSetupDialog|  
|PrintDialog|  
|ProgressBar|  
|RadioButton|  
|RichTextBox|  
|SaveFileDialog|  
|ScrollableControl|  
|SoundPlayer|  
|StatusBar|  
|TabControl/TabPage|  
|TextBox|  
|計時器|  
|ToolBar|  
|ToolTip|  
|TrackBar|  
|TreeView|  
|VscrollBar|  
|Web 瀏覽器|  
  
 下列控制項只會透過 Microsoft Active Accessibility 的支援來公開 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]。 部分功能可能無法使用。  
  
|控制項名稱|  
|------------------|  
|BindingSource|  
|DataGrid|  
|DataGridView|  
|DataNavigator|  
|DomainUpDown|  
|ErrorProvider|  
|FlowLayoutPanel|  
|表單|  
|LinkLabel|  
|HelpProvider|  
|MaskedTextBox|  
|MenuStrip/ContextMenuStrip|  
|NumericUpDown|  
|面板|  
|PictureBox|  
|PrintDocument|  
|PrintPreview-Control|  
|PrintPreview-Dialog|  
|PropertyGrid|  
|UserControl|  
|ToolStrip|  
|TableLayoutPanel|  
|SplitContainer/SplitterPanel|  
|分隔器|  
|RaftingContainer|  
|StatusStrip|  
  
## <a name="see-also"></a>請參閱

- [UI 自動化控制項類型](ui-automation-control-types.md)
