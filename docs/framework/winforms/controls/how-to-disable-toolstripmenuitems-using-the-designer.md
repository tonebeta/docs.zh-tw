---
title: "如何：使用設計工具停用 ToolStripMenuItems"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f704e99622900d8c37c8ddd5054a3c5ad920bc6b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a>如何：使用設計工具停用 ToolStripMenuItems
您可以限制或擴大使用者可能會進行啟用及停用功能表項目，以回應使用者活動的命令。 依預設會啟用功能表項目，建立，但這可以透過調整<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性。 您可以操作此屬性在設計階段於**屬性**視窗或以程式設計方式在程式碼中設定。 如需詳細資訊，請參閱[如何： 停用 ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-disable-a-menu-item-at-design-time"></a>若要在設計階段停用功能表項目  
  
1.  表單上選取功能表項目，設定<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性`false`。  
  
    > [!TIP]
    >  停用功能表中的第一個或最上層功能表項目，就會停用功能表內包含的所有功能表項目。 同樣地，停用功能表項目具有子功能表項目停用子功能表項目。 如果使用者無法使用指定的功能表上的所有命令，它會視為良好的程式設計作法，同時隱藏和停用整個功能表中，這會清除使用者介面。 您應該同時隱藏及停用功能表上，單獨隱藏攠摝坫透過功能表命令不會防止存取。 設定<xref:System.Windows.Forms.ToolStripItem.Visible%2A>屬性的最上層功能表項目`false`隱藏整個功能表。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [操作說明：隱藏 ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [MenuStrip 控制項概觀](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
