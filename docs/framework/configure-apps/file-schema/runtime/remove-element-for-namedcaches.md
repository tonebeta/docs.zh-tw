---
title: "&lt;移除&gt;元素&lt;namedCaches&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4b360b206586b263627ab6f6b7e0309f3055f38a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a>&lt;移除&gt;元素&lt;namedCaches&gt;
從記憶體快取的 `namedCaches` 集合移除具名快取項目。  
  
 \<system.runtime.caching >  
\<memoryCache >  
\<namedCaches >  
\<移除 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>類型  
 `None`  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 `None`  
  
### <a name="child-elements"></a>子項目  
 `None`  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|包含集合的組態設定具名<xref:System.Runtime.Caching.MemoryCache>執行個體。|  
  
## <a name="remarks"></a>備註  
 `remove`項目會移除`namedCache`從記憶體快取具名快取集合的項目。  
  
## <a name="see-also"></a>請參閱  
 [\<namedCaches > 項目 （快取設定）](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
