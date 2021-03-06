---
title: "ICorDebugHeapValue2::CreateHandle 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue2.CreateHandle
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eeef3215c3740cdaa7d1b78b73fde9e76d7b40c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue2createhandle-method"></a>ICorDebugHeapValue2::CreateHandle 方法
建立這個 ICorDebugHeapValue2 物件所代表的堆積值的指定類型的控制代碼。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
#### <a name="parameters"></a>參數  
 `type`  
 [in]CorDebugHandleType 列舉，指定建立控制代碼類型的值。  
  
 `ppHandle`  
 [out]ICorDebugHandleValue 物件，表示新控制代碼，此堆積值的位址指標。  
  
## <a name="remarks"></a>備註  
 控制代碼會在堆積的值，與相關聯的應用程式定義域中建立，且會變成無效，如果應用程式定義域卸載。  
  
 多次呼叫此函式相同的堆積值將會建立多個控制代碼。 控制代碼會影響記憶體回收行程的效能，因為偵錯工具應該限制為本身相對較小的數字的時間在使用中的控制代碼 (大約 256)。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
