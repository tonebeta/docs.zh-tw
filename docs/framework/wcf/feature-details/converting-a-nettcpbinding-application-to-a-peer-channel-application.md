---
title: "將 NetTcpBinding 應用程式轉換為對等通道應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ee46e34aea14c4ee9ce23c807170104173f2704
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>將 NetTcpBinding 應用程式轉換為對等通道應用程式
您可以使用會描述連線參數的繫結，在使用 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] 的用戶端之間建立連線。 轉換 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 應用程式以使用對等連線時，會需要在進行用戶端連線時支援此技術的繫結。 對等通道會提供名稱為 <xref:System.ServiceModel.NetPeerTcpBinding> 的繫結，其使用方法類似於使用 <xref:System.ServiceModel.NetTcpBinding>。 之間的主要差異則包括指定解析程式服務和定義安全性設定。  
  
 如果應用程式使用預設解析程式和安全性設定，轉換正常用戶端/伺服器型應用程式以使用對等通道則牽涉到在應用程式的組態檔中將繫結的名稱從 "NetTcpBinding" 變更為 "NetPeerTcpBinding"，而您並不需要變更應用程式的程式碼基礎。  
  
## <a name="see-also"></a>請參閱  
 [建置對等通道應用程式](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)  
 [系統提供的繫結](../../../../docs/framework/wcf/system-provided-bindings.md)
