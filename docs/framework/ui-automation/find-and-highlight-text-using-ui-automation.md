---
title: 使用 UI 自动化查找和突出显示文本
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text, highlighting
- finding text
- text, finding
- UI automation, highlighting text
- UI automation, finding text
- highlighting text
ms.assetid: b77693f5-87bb-4b29-a297-05ff882e2044
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 7229c9468948061726e81e3c79d2ab56e7497fa4
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858224"
---
# <a name="find-and-highlight-text-using-ui-automation"></a>使用 UI 自动化查找和突出显示文本
> [!NOTE]
>  本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。 有关最新信息[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，请参阅[Windows 自动化 API: UI 自动化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主题演示如何按顺序搜索并突出显示文本控件使用的内容中字符串的每个匹配项[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]。  
  
## <a name="example"></a>示例  
 以下示例获取<xref:System.Windows.Automation.TextPattern>文本控件中的对象。 一个<xref:System.Windows.Automation.Text.TextPatternRange>则使用创建对象，表示整个文档的文本内容<xref:System.Windows.Automation.TextPattern.DocumentRange%2A>属性的<xref:System.Windows.Automation.TextPattern>。 两个附加<xref:System.Windows.Automation.Text.TextPatternRange>对象创建顺序搜索和突出显示功能。  
  
 [!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
 [!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#SearchTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#searchtarget)]
[!code-vb[FindText#SearchTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#searchtarget)]  
  
## <a name="see-also"></a>请参阅  
 [使用 UI 自动化查找和突出显示文本](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
