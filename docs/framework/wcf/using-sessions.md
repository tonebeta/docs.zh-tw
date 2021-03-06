---
title: "使用工作階段"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: sessions [WCF]
ms.assetid: 864ba12f-3331-4359-a359-6d6d387f1035
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f5f6df22918dedf32738a8cb9d73af2e625923a4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="using-sessions"></a>使用工作階段
在 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 應用程式中，「 *工作階段* 」(Session) 會使一組訊息相互關連至對話。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 工作階段不同於 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 應用程式中可用的工作階段物件，而且支援不同的行為，控制的方式也不一樣。 本主題說明工作階段在 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 應用程式中啟用的功能及其用法。  
  
## <a name="sessions-in-windows-communication-foundation-applications"></a>Windows Communication Foundation 應用程式中的工作階段  
 當服務合約指定其需要工作階段時，該合約會指定所有的呼叫 (即支援呼叫的基礎訊息交換) 必須是同一個對話的一部分。 如果合約指定其允許使用工作階段，但不需要工作階段，則用戶端可以連線，並選擇是否要建立工作階段。 如果工作階段結束，而且某個訊息已透過相同的通道傳送，就會擲回例外狀況。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 工作階段在概念上有下列主要特色：  
  
-   工作階段是由呼叫的應用程式 (WCF 用戶端) 明確地啟始及終止。  
  
-   工作階段期間傳遞的訊息是依其接收的順序進行處理。  
  
-   工作階段會將一群訊息互相關聯為對話。 可能會有不同類型的相互關聯。 例如，某個工作階段架構通道可能會根據共用的網路連線將訊息相互關聯，而另一個工作階段架構通道可能會根據訊息本文內的共用標記將訊息相互關聯。 這些可以衍生自工作階段的功能視相互關聯的本質而定。  
  
-   沒有與 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 工作階段關聯的一般資料存放區。  
  
 如果您很熟悉 <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> 應用程式內的 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 類別及其所提供的功能，則您可能會注意到這類工作階段和 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 工作階段之間有下列不同之處：  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 工作階段一律由伺服器啟動。  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 工作階段具有隱含未排序特性。  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 工作階段提供了跨要求的一般資料儲存機制。  
  
 本主題內容：  
  
-   使用服務模型層中工作階段架構繫結時的預設執行行為。  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 之工作階段架構和系統提供繫結所提供的功能類型。  
  
-   如何建立會宣告工作階段需求的合約。  
  
-   如何了解並控制工作階段的建立與終止，以及工作階段與服務執行個體之間的關係。  
  
## <a name="default-execution-behavior-using-sessions"></a>使用工作階段的預設執行行為  
 會嘗試初始化工作階段的繫結稱為「 *工作階段架構* 」(Session-based) 繫結。 服務合約會指定其需要、允許，或拒絕工作階段架構繫結，方法是將服務合約介面 (或類別) 上的 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> 屬性設為其中一個 <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> 列舉值。 根據預設，這個屬性的值為 <xref:System.ServiceModel.SessionMode.Allowed>，表示如果用戶端使用工作階段架構繫結來搭配 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務實作，服務就會建立並使用所提供的工作階段。  
  
 當 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務接受用戶端工作階段時，依預設會啟用下列功能：  
  
1.  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端物件之間的所有呼叫都會由相同的服務執行個體處理。  
  
2.  不同的工作階段架構繫結會提供額外的功能。  
  
## <a name="system-provided-session-types"></a>系統提供的工作階段類型  
 工作階段架構繫結支援服務執行個體與特定工作階段之間的預設關聯。 然而，除了啟用先前所述的工作階段架構執行個體控制之外，不同的工作階段架構繫結也支援不同的功能。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 提供下列類型的工作階段架構應用程式行為：  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType> 支援安全性工作階段，其中通訊兩端均同意特定安全對話。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][保護服務](../../../docs/framework/wcf/securing-services.md)。 例如，<xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType> 繫結同時支援安全性工作階段與可靠工作階段，但根據預設，只會使用加密並以數位方式簽署訊息的安全工作階段。  
  
-   <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> 繫結支援 TCP/IP 架構工作階段，可確保所有訊息都在通訊端層級由連線建立相互關聯。  
  
-   <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> 項目會實作 WS-ReliableMessaging 規格，支援可在其中將訊息設定為依序傳遞且只傳遞一次的可靠工作階段，確保即使訊息在對話期間行經多個節點仍會收到訊息。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][可靠工作階段](../../../docs/framework/wcf/feature-details/reliable-sessions.md)。  
  
-   <xref:System.ServiceModel.NetMsmqBinding?displayProperty=nameWithType> 繫結提供 MSMQ 資料包工作階段。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][WCF 中的佇列](../../../docs/framework/wcf/feature-details/queues-in-wcf.md)。  
  
 設定 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> 屬性不會指定合約所需的工作階段類型，只代表它需要工作階段。  
  
## <a name="creating-a-contract-that-requires-a-session"></a>建立需要工作階段的合約  
 建立需要工作階段的合約表示服務合約所宣告的作業群組必須都在同一個工作階段中執行，而且必須依序傳遞訊息。 若要對服務合約所需要的工作階段支援層級進行判斷提示，請將您服務合約介面或類別的 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> 屬性設為 <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> 列舉的值，以指定合約是否：  
  
-   需要工作階段。  
  
-   允許用戶端建立工作階段。  
  
-   禁止工作階段。  
  
 但是，設定 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> 屬性不會指定合約所需的工作階段架構行為類型， 而會指示 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 在執行階段確認設定的服務繫結 (可建立通訊通道) 是否或可以在實作服務時建立工作階段。 同時，繫結可以其選擇的任何工作階段架構行為類型 (安全性、傳輸、可靠或某種組合) 滿足該需求， 實際的行為則視選取的 <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> 值而定。 如果設定的服務繫結不符合 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A>的值，就會擲回例外狀況。 支援工作階段的繫結及其建立的通道都稱為工作階段架構繫結和通道。  
  
 下列服務合約指定 `ICalculatorSession` 中的所有作業必須在工作階段中交換。 除了 `Equals` 方法以外，任何作業都不會將值傳回呼叫者。 然而， `Equals` 方法不會採用任何參數，因此只能在工作階段中傳回非零的值，而其中資料已經傳遞至其他作業。 此合約需要工作階段才能正確運作， 如果缺乏與特定用戶端關聯的工作階段，服務執行個體便無法得知此用戶端先前傳送了哪些資料。  
  
 [!code-csharp[S_Service_Session#1](../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
 如果服務允許使用工作階段，則會在用戶端初始化工作階段後建立一個工作階段並加以使用；否則，將不會建立任何工作階段。  
  
## <a name="sessions-and-service-instances"></a>工作階段與服務執行個體  
 如果您使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]中的預設執行個體行為， [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端物件之間的所有呼叫都會由相同的服務執行個體來處理。 因此，在應用程式層級，您可以將工作階段視為一個類似本機呼叫行為的啟用應用程式行為。 例如，當您建立本機物件時：  
  
-   會呼叫建構函式。  
  
-   所有對 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端物件參考進行的後續呼叫都會由相同的物件執行個體來處理。  
  
-   會在終結物件參考時呼叫解構函式 (Destructor)。  
  
 只要是使用預設的服務執行個體行為，工作階段就會在用戶端與服務之間啟用類似的行為。 如果服務合約需要或支援工作階段，您可以設定 <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A> 和 <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A> 屬性，將一或多個合約作業標示為初始化工作階段或終止工作階段。  
  
 「*初始化作業* 」(Initiating Operation) 是指必須當做新工作階段第一個作業呼叫的作業。 只有在已呼叫至少一個初始化作業後才能呼叫非初始化作業。 因此，您可以宣告設計用來接收服務執行個體開頭適用之用戶端輸入的初始化作業，為服務建立一種工作階段建構函式 (但是，狀態會與工作階段而非服務物件相關聯)。  
  
 相反地，「*終止作業*」(Terminating Operation) 則必須當做現有工作階段的最後一則訊息來呼叫。 在預設案例中， [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 會在與服務關聯的工作階段關閉後回收服務物件及其內容。 因此，您可以宣告設計用來執行服務執行個體結尾適用之函式的終止作業，藉此建立一種解構函式。  
  
> [!NOTE]
>  雖然預設行為與本機建構函式和解構函式有相似之處，但也只是相似而已。 任何 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務作業都可以是初始化或終止作業，或兩者皆是。 此外，在預設案例中，您可以不按次序且不限次數地呼叫啟始作業。一旦建立工作階段並使其與執行個體產生關聯，就不能再建立其他工作階段，除非您明確地控制服務執行個體的存留期 (管理 <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> 物件)。 最後，狀態會與工作階段而非服務物件相關聯。  
  
 例如，先前範例中使用的 `ICalculatorSession` 合約要求 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端物件在呼叫其他任何作業之前先呼叫 `Clear` 作業，而且包含此 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端物件的工作階段應該在它呼叫 `Equals` 作業時終止。 下列程式碼範例示範強制執行這些要求的合約。 必須先呼叫`Clear` ，才能起始工作階段，而該工作階段會在呼叫 `Equals` 時結束。  
  
 [!code-csharp[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.isinitiatingisterminating/cs/service.cs#1)]
 [!code-vb[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.isinitiatingisterminating/vb/service.vb#1)]  
  
 服務不會啟動用戶端的工作階段。 在 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端應用程式中，工作階段架構通道的存留期和工作階段本身的存留期之間存在直接關係。 因此，用戶端會藉由建立新的工作階段架構通道來建立新工作階段，然後適當地關閉工作階段架構通道來終止現有的工作階段。 用戶端會呼叫下列其中一項，藉此啟動服務端點的工作階段：  
  
-   通道上藉由呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> 所傳回的 <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>。  
  
-   <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType>在[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]所產生的用戶端物件[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。  
  
-   針對任何一個 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端物件型別的初始化作業 (根據預設，所有作業都是初始化作業)。 呼叫第一個作業之後， [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端物件就會自動開啟通道並初始化工作階段。  
  
 一般來說，用戶端會呼叫下列其中一項，藉此結束服務端點的工作階段：  
  
-   通道上藉由呼叫 <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> 所傳回的 <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>。  
  
-   透過 Svcutil.exe 所產生之 <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType> 用戶端物件上的 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]。  
  
-   針對任何一個 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端物件型別的終止作業 (根據預設，所有作業都不是終止作業，合約必須明確指定終止作業)。 呼叫第一個作業之後， [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端物件就會自動開啟通道並初始化工作階段。  
  
 如需範例，請參閱 [How to: Create a Service That Requires Sessions](../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md) 、 [Default Service Behavior](../../../docs/framework/wcf/samples/default-service-behavior.md) 和 [Instancing](../../../docs/framework/wcf/samples/instancing.md) 範例。  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]用戶端與工作階段，請參閱[使用 WCF 用戶端存取服務](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)。  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>與 InstanceContext 設定互動的工作階段  
 合約內的 <xref:System.ServiceModel.SessionMode> 列舉與 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> 屬性之間會進行互動，以控制通道和特定服務物件之間的關聯。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][工作階段中，執行個體與並行](../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)。  
  
### <a name="sharing-instancecontext-objects"></a>共用 InstanceContext 物件  
 您也可以自行執行該關聯，以控制哪個工作階段架構通道或呼叫與哪個 <xref:System.ServiceModel.InstanceContext> 物件關聯。 如需完整範例，請參閱[InstanceContextSharing](http://msdn.microsoft.com/library/4a6a46d7-b7d7-4bb5-a0dd-03ffa3cbc230)。  
  
## <a name="sessions-and-streaming"></a>工作階段和資料流  
 當您有大量資料要傳輸時，除了將記憶體中的訊息全部經過緩衝並處理的預設行為外，也可以使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 中的資料流傳輸模式。 使用工作階段架構繫結對呼叫進行資料流處理時，可能會遇到未預期的行為。 即使使用的繫結已設定為使用工作階段，所有資料流處理呼叫還是會透過不支援工作階段的單一通道 (資料包通道) 來進行。 如果多個用戶端透過工作階段架構繫結對同一個服務物件進行資料流處理呼叫，而且服務物件的並行模式已設為單一且其執行個體內容模式已設為 `PerSession`，則所有呼叫必須經過資料包通道，所以一次只能處理一個呼叫。 一或多個用戶端可能會因此逾時。您可以將服務物件的 `InstanceContextMode` 設為 `PerCall` 或是將並行模式設為多重來解決這個問題。  
  
> [!NOTE]
>  此時 MaxConcurrentSessions 沒有作用，因為只有一個可用的「工作階段」。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A>
