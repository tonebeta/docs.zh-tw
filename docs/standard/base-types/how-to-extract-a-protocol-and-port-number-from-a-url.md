---
title: "如何：從 URL 擷取通訊協定和通訊埠編號"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: ab7f62b3-6d2c-4efb-8ac6-28600df5fd5c
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 10ab05ac8b24c0658be2f27809137c6b0bd4834f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>如何：從 URL 擷取通訊協定和通訊埠編號
下列範例會從 URL 擷取通訊協定和連接埠號碼。  
  
## <a name="example"></a>範例  
 此範例會使用<xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>方法傳回的通訊協定，後面接著冒號，後面接著的連接埠號碼。  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 規則運算式模式 `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` 的解譯方式如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`^`|在字串開頭開始比對。|  
|`(?<proto>\w+)`|比對一個或多個文字字元。 將此群組命名`proto`。|  
|`://`|比對冒號加兩個斜線符號。|  
|`[^/]+?`|比對一個或多個 (但越少越好) 出現的任何字元，但不包括斜線符號。|  
|`(?<port>:\d+)?`|比對零個或一個出現的冒號外加一個或多個數字字元。 將此群組命名`port`。|  
|`/`|比對斜線符號。|  
  
 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>方法會展開`${proto}${port}`取代順序，串連的兩個具名群組擷取規則運算式模式中的值。 它是方便的替代選項明確地串連字串所傳回的集合物件擷取<xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>屬性。  
  
 此範例會使用<xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>具有兩個替代項目，方法`${proto}`和`${port}`、 將擷取的群組包含在輸出字串。 您可以從比對擷取的擷取的群組<xref:System.Text.RegularExpressions.GroupCollection>相反地，下列程式碼所示的物件。  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 [.NET 規則運算式](../../../docs/standard/base-types/regular-expressions.md)
