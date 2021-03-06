---
title: "&gt;= 運算子 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '>=_CSharpKeyword'
helpviewer_keywords:
- greater than or equal to operator (>=) [C#]
- '>= operator [C#]'
ms.assetid: 0db4dcaf-56a3-4884-a7ad-35f64978a58d
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f020c2bd8756899908681ab72cac7aa2a203c6a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="gt-operator-c-reference"></a>&gt;= 運算子 (C# 參考)
如果第一個運算元大於或等於第二個運算元，則所有數值和列舉類型都會定義「大於或等於」關係運算子 (`>=`) 以傳回 `true`，否則為 `false`。  
  
## <a name="remarks"></a>備註  
 使用者定義型別可以多載 `>=` 運算子。 如需詳細資訊，請參閱[運算子](../../../csharp/language-reference/keywords/operator.md)。 如果多載 `>=`，也必須多載 [<=](../../../csharp/language-reference/operators/less-than-equal-operator.md)。 整數類資料類型上的作業通常允許用於列舉型別。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#39](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-equal-operator_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)
