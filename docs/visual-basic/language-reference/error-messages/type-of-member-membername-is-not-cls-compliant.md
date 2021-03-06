---
title: "型別成員 &#39;&lt;membername&gt;&#39; 不符合 CLS 標準"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords: BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bc82714d25efbe9d379fff36f92261cf25a78862
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="type-of-member-39ltmembernamegt39-is-not-cls-compliant"></a>型別成員 &#39;&lt;membername&gt;&#39; 不符合 CLS 標準
指定不是這個成員的資料類型屬於[語言獨立性以及與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md)（cls） 標準。 這是不在您的元件中發生錯誤，因為[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]和[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]支援這種資料類型。 不過，另一個以完全符合 CLS 標準的程式碼撰寫的元件可能不支援這種資料類型。 這類元件可能無法順利互動與您的元件。  
  
 下列 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 資料類型不符合 CLS 標準：  
  
-   [SByte 資料類型](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger 資料類型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong 資料類型](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort 資料類型](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC40025  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果您的元件介面只能與其他[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]元件或不與其他任何元件介面，您不需要變更任何項目。  
  
-   如果您要使用的元件不是針對撰寫的[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]，您可以判斷，可能是透過反映或文件，是否支援此資料類型。 若是如此，您不需要變更任何項目。  
  
-   如果您要使用的元件，不支援這種資料類型的您必須將它取代接近符合 CLS 標準的類型。 例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。 如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。  
  
-   如果您要與 Automation 或 COM 物件進行互動，請記住，某些型別的資料寬度會與在 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 中的資料寬度不同。 例如，`uint` 在其他環境中通常是 16 位元。 如果您要將 16 位元引數至這類元件，將它宣告為`UShort`而不是`UInteger`中 managed[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]程式碼。  
  
## <a name="see-also"></a>請參閱  
 [反映](../../../framework/reflection-and-codedom/reflection.md)  
 
