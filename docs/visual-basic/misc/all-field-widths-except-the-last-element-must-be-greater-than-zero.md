---
title: "除了最後項目以外的所有欄位寬度都必須大於零"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrTextFieldParser_FieldWidthsMustPositive
ms.assetid: 41d8c661-a749-4c89-be56-905c6e7c3c9d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b348494c0a3103641d29998218b546de0d432e2a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="all-field-widths-except-the-last-element-must-be-greater-than-zero"></a>除了最後項目以外的所有欄位寬度都必須大於零
除了最後項目以外的所有欄位寬度都必須大於零。 最後項目的欄位寬度小於或等於零，表示最後欄位是可變長度。  
  
 作業失敗，因為除了最後項目以外的欄位寬度都設定為等於或小於零。 小於或等於零的欄位寬度可以用作最後項目，表示最後欄位是可變長度，但不能用作任何其他項目。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   將欄位寬度設定為正確的長度。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths>  
 [如何：從固定寬度的文字檔讀取](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [TextFieldParser 物件](../../visual-basic/language-reference/objects/textfieldparser-object.md)
