---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf90e78ed7fbfe500ac52e6629d31bd0aff97bd8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a>3552 - MaxPendingMessagesPerChannelExceeded
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|ID|3552|  
|關鍵字|配額、WFServices|  
|層級|警告|  
|通道|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  
 表示已達到節流 'MaxPendingMessagesPerChannel' 限制。  
  
## <a name="message"></a>訊息  
 已達到節流 'MaxPendingMessagesPerChannel' 限制為 '%1'。 若要增加此限制，請調整 BufferedReceiveServiceBehavior 上的 MaxPendingMessagesPerChannel 屬性。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|限制|xs:string|已達到 MaxPendingMessagesPerChannel 節流的限制。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
