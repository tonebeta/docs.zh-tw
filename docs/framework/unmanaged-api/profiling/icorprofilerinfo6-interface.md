---
title: "ICorProfilerInfo6 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfilerInfo6
api_location: mscorwks.dll
api_type: COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 805f1e451b2c13c356d904c42dff87304aa2093c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo6-interface"></a>ICorProfilerInfo6 介面
[在.NET Framework 4.6 和更新版本中支援]  
  
 子類別[ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)可提供給定的 NGen 模組和內嵌指定的方法中所定義的所有方法的列舉值。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|傳回屬於指定的 NGen 模組，以及屬於給定方法主體中內嵌的所有方法的列舉值。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
