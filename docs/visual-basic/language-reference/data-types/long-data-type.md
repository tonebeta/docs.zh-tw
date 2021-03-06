---
title: "Long 資料類型 (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e21ed43ddc6efb018df0581faed1ebf270ab3ca
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="long-data-type-visual-basic"></a>Long 資料類型 (Visual Basic)

保存帶正負號的 64 位元 （8 個位元組） 整數值範圍從-9223372036854775808 到 9,223,372,036,854,775,807 (9.2 … E + 18)。  
  
## <a name="remarks"></a>備註

 使用`Long`資料類型可包含整數的數字太大，無法納入`Integer`資料型別。  
  
 `Long` 的預設值為 0。

## <a name="literal-assignments"></a>常值的指派 

您可以宣告和初始化`Long`變數將其指派十進位常值、 十六進位常值、 八進位常值，或是 （從開始使用 Visual Basic 2017） 二進位常值。 如果整數常值超出 `Long` 的範圍 (亦即，如果小於 <xref:System.Int64.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Int64.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。

在下列範例中，如果整數等於 4,294,967,296，即表示 `Long` 值指派了十進位、十六進位和二進位常值。
  
[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]  

> [!NOTE]
> 使用前置詞`&h`或`&H`來表示十六進位常值前置詞`&b`或`&B`代表二進位常值，以及前置詞`&o`或`&O`代表八進位常值。 十進位常值沒有前置詞。

從 Visual Basic 2017 開始，您也可以使用底線字元， `_`，當做數字分隔符號，以提升可讀性，如下列範例所示。

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

數值常值也可以包含`L`[類型字元](../../programming-guide\language-features\data-types/type-characters.md)代表`Long`資料類型，如下列範例所示。

```vb
Dim number = &H0FAC0326L
```

## <a name="programming-tips"></a>程式設計提示

-   **Interop 考量。** 如果您要使用的元件不是撰寫.NET framework，例如 Automation 或 COM 物件，請記住，`Long`在其他環境中都有不同的資料寬度 （32 位元）。 如果您要將 32 位元引數至這類元件，將它宣告為`Integer`而不是`Long`新的 Visual Basic 程式碼。  
  
-   **擴展。** `Long`資料類型可擴展成`Decimal`， `Single`，或`Double`。 這表示，您可以將 `Long` 轉換成這些類型的任何一種，而不會發生 <xref:System.OverflowException?displayProperty=nameWithType> 錯誤。  
  
-   **類型字元。** 將常值類型字元 `L` 附加到常值，會強制其成為 `Long` 資料類型。 將識別項類型字元 `&` 附加到任何識別項，會強制其成為 `Long`。  
  
-   **架構類型。** 在 .NET Framework 中對應的類型為 <xref:System.Int64?displayProperty=nameWithType> 結構。  

## <a name="see-also"></a>請參閱

<xref:System.Int64>[資料類型](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
[整數資料類型](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
[Short 資料類型](../../../visual-basic/language-reference/data-types/short-data-type.md)   
[類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
[轉換的摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
[有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
