---
title: 操作說明：從繫結的目標屬性取得繫結物件
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: cf2ddc93a7c46ee6956d2731a786289f64086360
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976426"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>操作說明：從繫結的目標屬性取得繫結物件
這個範例顯示如何從資料繫結目標屬性取得繫結物件。

## <a name="example"></a>範例
 您可以執行下列動作來取得 <xref:System.Windows.Data.Binding> 物件：

 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]

> [!NOTE]
> 因為目標物件可能有多個屬性使用資料繫結，所以必須指定所要繫結的相依性屬性。

 或者，您可以取得 <xref:System.Windows.Data.BindingExpression>，然後取得 <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> 屬性的值。

 如需完整範例，請參閱[繫結驗證範例 (英文)](https://go.microsoft.com/fwlink/?LinkID=159972)。

> [!NOTE]
> 如果您的系結是 <xref:System.Windows.Data.MultiBinding>，請使用 <xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A?displayProperty=nameWithType>。 如果是 <xref:System.Windows.Data.PriorityBinding>，請使用 <xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A?displayProperty=nameWithType>。 如果您不確定目標屬性是使用 <xref:System.Windows.Data.Binding>、<xref:System.Windows.Data.MultiBinding>或 <xref:System.Windows.Data.PriorityBinding>來系結，您可以使用 <xref:System.Windows.Data.BindingOperations.GetBindingBase%2A?displayProperty=nameWithType>。

## <a name="see-also"></a>請參閱

- [使用程式碼建立繫結](how-to-create-a-binding-in-code.md)
- [「如何」主題](data-binding-how-to-topics.md)
