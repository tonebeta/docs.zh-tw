---
title: "取得 UI 自動化項目屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
caps.latest.revision: "5"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f3fcbb25fab616b60a1f60d9443af13b60f2d27a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="get-ui-automation-element-properties"></a>取得 UI 自動化項目屬性
> [!NOTE]
>  這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題示範如何擷取屬性的[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]項目。  
  
### <a name="get-a-current-property-value"></a>取得目前的屬性值  
  
1.  取得<xref:System.Windows.Automation.AutomationElement>您想要取得其屬性。  
  
2.  呼叫<xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>，或擷取<xref:System.Windows.Automation.AutomationElement.Current%2A>屬性結構，以及如何取得其成員的值。  
  
### <a name="get-a-cached-property-value"></a>取得快取的屬性值  
  
1.  取得<xref:System.Windows.Automation.AutomationElement>您想要取得其屬性。 屬性必須具有在指定<xref:System.Windows.Automation.CacheRequest>。  
  
2.  呼叫<xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>，或擷取<xref:System.Windows.Automation.AutomationElement.Cached%2A>屬性結構，以及如何取得其成員的值。  
  
## <a name="example"></a>範例  
 下列範例示範各種方式來擷取目前的屬性<xref:System.Windows.Automation.AutomationElement>。  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>請參閱  
 [用戶端的 UI 自動化屬性](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
 [在 UI 自動化中使用快取](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [UI 自動化用戶端中的快取](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
