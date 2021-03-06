---
title: "ResolveTypeLib 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ResolveTypeLib
api_location: tlbref.dll
f1_keywords: ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72d1cedbfc1a1ec6c3588a7b0be9cf657d7369fd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="resolvetypelib-method"></a>ResolveTypeLib 方法
藉由傳回其完整的路徑來解析類型程式庫的簡單名稱。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
#### <a name="parameters"></a>參數  
 `bstrSimpleName`  
 [in]A [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) ，其中包含的類型程式庫的簡單名稱。  
  
 `tlbid`  
 [in]指派給類型程式庫中登錄的 GUID。  
  
 `lcid`  
 [in]當地語系化類型程式庫的識別碼。  
  
 `wMajorVersion`  
 [in]類型程式庫的主要版本號碼。 例如，針對版本*x.y*，主要版本號碼是*x*。  
  
 `wMinorVersion`  
 [in]類型程式庫的次要版本號碼。 例如，針對版本*x.y*，次要版本號碼是*y*。  
  
 `syskind`  
 [in]A [SYSKIND](http://msdn.microsoft.com/library/662048b2-59a8-48ca-9e4f-2f9a5306faa1)識別的作業環境的旗標。 常見的值為 SYS_WIN32 和 SYS_WIN64。  
  
 `pbstrResolvedTlbName`  
 [out]指標[BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) ，其中包含名為中的類型程式庫的完整路徑`bstrSimpleName`參數。  
  
## <a name="remarks"></a>備註  
 `ResolveTypeLib`方法透過呼叫[LoadTypeLibWithResolver 函式](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)期間[Tlbexp.exe （類型程式庫匯出工具）](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)處理。  
  
 此介面的自訂實作必須傳回[BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) ，其中包含名為中的類型程式庫的完整路徑`bstrSimpleName`參數。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** TlbRef.idl、 TlbRef.h  
  
 **程式庫：** TlbRef.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [Tlbexp Helper 函式](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [LoadTypeLibEx](http://msdn.microsoft.com/library/56a7f9e1-810b-4a42-aa4d-691f4304f5ef)
