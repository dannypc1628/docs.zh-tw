---
title: 如何：使用應用程式範圍的資源字典
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 5bfb3ed0304598a5acf4b7682bf4a4169c5153d1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459792"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a>如何：使用應用程式範圍的資源字典
此範例示範如何定義和使用應用程式範圍自訂資源字典。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Application> 會公開共用資源的應用程式範圍存放區： <xref:System.Windows.Application.Resources%2A>。 根據預設，<xref:System.Windows.Application.Resources%2A> 屬性會使用 <xref:System.Windows.ResourceDictionary> 類型的實例進行初始化。 當您使用 <xref:System.Windows.Application.Resources%2A>取得和設定應用程式範圍的屬性時，會使用這個實例。 如需詳細資訊，請參閱[如何：取得和設定應用程式範圍的資源](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100))。
  
 如果您有多個使用 <xref:System.Windows.Application.Resources%2A>設定的資源，您可以改為使用自訂資源字典來儲存這些資源，並改為設定 <xref:System.Windows.Application.Resources%2A>。 以下顯示如何使用 XAML 宣告自訂資源字典。
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 使用 <xref:System.Windows.Application.Resources%2A> 交換整個資源字典可讓您支援應用程式範圍主題，其中每個主題都是由單一資源字典封裝。 下列範例會示範如何設定 <xref:System.Windows.ResourceDictionary>。  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 以下顯示如何從 XAML 中 <xref:System.Windows.Application.Resources%2A> 所公開的資源字典取得應用程式範圍的資源。  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 下列會顯示也可以如何使用程式碼來取得資源。  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 使用 <xref:System.Windows.Application.Resources%2A>時，需要進行兩個考慮。 首先，字典索引*鍵*是物件，因此當您設定並取得屬性值時，必須使用完全相同的物件實例。 （請注意，使用字串時，索引鍵會區分大小寫）。第二，字典*值*是物件，因此，您必須在取得屬性值時，將值轉換成所需的類型。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [合併的資源字典](../advanced/merged-resource-dictionaries.md)
