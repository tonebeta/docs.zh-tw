---
title: "外部索引鍵屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 044be77cbbd8b5ad16cfbd5bbf1fdde984a060d5
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="foreign-key-property"></a>外部索引鍵屬性
A*外部索引鍵屬性*實體資料模型 (EDM) 中是基本型別[屬性](../../../../docs/framework/data/adonet/property.md)（或基本型別屬性的一組） 上[實體類型](../../../../docs/framework/data/adonet/entity-type.md)包含[實體索引鍵](../../../../docs/framework/data/adonet/entity-key.md)另一個實體類型。  
  
 外部索引鍵屬性類似關聯式資料庫中的外部索引鍵資料行。 外部索引鍵資料行用於建立資料表中的資料列之間的關聯性的關聯式資料庫的相同方式，在概念模型中的外部索引鍵屬性用來建立[關聯](../../../../docs/framework/data/adonet/association-type.md)實體類型之間。 A[參考完整性條件約束](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)用來定義兩個實體類型，當其中一個型別具有外部索引鍵屬性之間的關聯。  
  
## <a name="example"></a>範例  
 下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。 `Book` 實體類型具有屬性 `PublisherId`，當您定義 `Publisher` 關聯的參考完整性條件約束時，此屬性會參考 `PublishedBy` 實體類型的實體索引鍵。  
  
 ![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。 下列 CSDL 使用外部索引鍵屬性 `PublisherId`，針對上述概念模型中的 `PublishedBy` 關聯定義參考完整性條件約束。  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>請參閱  
 [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)
