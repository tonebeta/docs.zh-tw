---
title: "設定用於 Windows Communication Foundation 的 Windows Process Activation Service"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12df9e3760774b4dc8d4e8f73a09df5e79c2453e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a>設定用於 Windows Communication Foundation 的 Windows Process Activation Service
本主題說明設定 [!INCLUDE[wv](../../../../includes/wv-md.md)] 中 Windows Process Activation Service (亦稱為 WAS) 來裝載無法透過 HTTP 網路通訊協定進行通訊的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務時所需的步驟。 下列各節將概述此組態的各項步驟：  
  
-   安裝 (或確認安裝) 所需的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動元件。  
  
-   運用您希望使用的網路通訊協定繫結來建立 WAS 網站，或是將新通訊協定繫結新增至現有網站。  
  
-   建立應用程式來裝載服務，並啟用該應用程式來使用所需的網路通訊協定。  
  
-   建置可公開非 HTTP 端點的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。  
  
## <a name="configuring-a-site-with-non-http-bindings"></a>使用非 HTTP 繫結來設定網站  
 若要以非 HTTP 繫結來搭配 WAS 一起使用，必須將網站繫結新增至 WAS 組態。 WAS 的組態存放區就是 applicationHost.config 檔 (位於 %windir%\system32\inetsrv\config 目錄)。 這個組態存取區可由 WAS 和 IIS 7.0 同時共用。  
  
 applicationHost.config 是一個可使用任何標準文字編輯器 (例如 [記事本]) 來開啟的 XML 文字檔。 但是，我們建議您使用 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 命令列組態工具 (appcmd.exe) 來新增非 HTTP 的網站繫結。  
  
 下列命令會使用 appcmd.exe 將 net.tcp 網站繫結新增至預設的網站 (此命令需以單行方式輸入)。  
  
```  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 此命令會將下列所示字行新增至 applicationHost.config 檔，以將新的 net.tcp 繫結新增至預設的網站。  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
        <bindings>  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            //The following line is added by the command.  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
        </bindings>  
    </site>  
</sites>  
```  
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a>啟用應用程式來使用非 HTTP 通訊協定  
 您可以啟用或停用個別的網路 protocolsat 應用程式層級。 下列命令說明如何針對在 `Default Web Site` 中執行的應用程式同時啟用 HTTP 和 net.tcp 通訊協定。  
  
```  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 啟用的通訊協定清單也可以設定\<透過 > 項目儲存在 ApplicationHost.config 中的站台的 XML 組態。  
  
 下列來自 applicationHost.config 的 XML 程式碼說明同時繫結至 HTTP 和非 HTTP 通訊協定的網站。 支援非 HTTP 通訊協定所需的額外組態可以藉由註解來呼叫。  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
    <application path="/">  
        <virtualDirectory path="/" physicalPath="D:\inetpub\wwwroot" />  
    </application>  
       <bindings>  
            //The following two lines are added by the command.  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
       </bindings>  
    </site>  
    <siteDefaults>  
        <logFile   
        customLogPluginClsid="{FF160663-DE82-11CF-BC0A-00AA006111E0}"  
          directory="D:\inetpub\logs\LogFiles" />  
        <traceFailedRequestsLogging   
          directory="D:\inetpub\logs\FailedReqLogFiles" />  
    </siteDefaults>  
    <applicationDefaults   
      applicationPool="DefaultAppPool"   
      //The following line is inserted by the command.  
      enabledProtocols="http, net.tcp" />  
    <virtualDirectoryDefaults allowSubDirConfig="true" />  
</sites>  
```  
  
 如果您嘗試使用 WAS 進行非 HTTP 啟用以啟動服務，但是尚未安裝並設定 WAS，您可能會看到以下錯誤：  
  
```Output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 如果您收到這個錯誤，請確認已安裝並正確設定適用於非 HTTP 啟用的 WAS。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][如何： 安裝及設定 WCF 啟用元件](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)。  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a>針對非 HTTP 啟動建置使用 WAS 的 WCF 服務  
 在您執行的步驟來安裝和設定 WAS 後 (請參閱[如何： 安裝及設定 WCF 啟用元件](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md))，設定服務來使用 WAS 啟動是類似於在 IIS 中設定裝載的服務。  
  
 如需有關建立 WAS 啟動的詳細指示[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務，請參閱[How to： 將 WCF 服務裝載於 WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)。  
  
## <a name="see-also"></a>請參閱  
 [在 Windows 處理序啟用服務中裝載](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)  
 [Windows Server App Fabric 裝載功能](http://go.microsoft.com/fwlink/?LinkId=201276)
