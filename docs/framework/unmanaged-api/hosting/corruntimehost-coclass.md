---
title: CorRuntimeHost Coclass
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorRuntimeHost Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CorRuntimeHost
helpviewer_keywords: CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23bee1a79dfb54a696495fdb61a7ba9ba4b4c143
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corruntimehost-coclass"></a>CorRuntimeHost Coclass
提供介面來管理 common language runtime 所執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a>介面  
  
|介面|描述|  
|---------------|-----------------|  
|[ICorConfiguration 介面](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|提供方法來設定 common language runtime (CLR)。|  
|[ICorRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|提供方法，讓主應用程式啟動和停止 common language runtime 明確地建立和設定應用程式定義域，若要存取的預設網域，並列舉處理序中執行的所有網域。|  
|[IDebuggerInfo 介面](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|提供方法來取得有關偵錯服務的狀態資訊。|  
|[IGCHost 介面](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|提供方法來取得記憶體回收系統的相關資訊，以及控制記憶體回收的某些層面。|  
|「 IValidator"|提供方法進行驗證的可攜式執行檔影像，並驗證錯誤的詳細報告。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.idl  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [裝載 Coclass](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
