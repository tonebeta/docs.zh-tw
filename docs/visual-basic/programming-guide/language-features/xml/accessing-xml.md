---
title: "在 Visual Basic 中存取 XML"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 79c7b8a94731e151a803a041d91dd1e240ddeb97
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="accessing-xml-in-visual-basic"></a>在 Visual Basic 中存取 XML
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]XML 軸屬性提供用於存取和導覽[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]結構。 這些屬性會使用特殊的語法，可讓您指定的 XML 名稱來存取項目和屬性。  
  
 下表列出可讓您存取 XML 元素和屬性中的語言功能[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]。  
  
### <a name="xml-axis-properties"></a>XML 軸屬性  
  
|屬性描述|範例|說明|  
|--------------------------|-------------|-----------------|  
|*子軸*|`contact.<phone>`|取得所有`phone`子項目數的項目`contact`項目。|  
|*屬性軸*|`phone.@type`|取得所有`type`屬性`phone`項目。|  
|*descendant 軸*|`contacts...<name>`|取得所有`name`的項目`contacts`項目，不論它們出現在階層中深度。|  
|*擴充索引子*|`contacts...<name>(0)`|取得第一個`name`序列中的項目。|  
|*value*|`contacts...<name>.Value`|取得第一個物件的字串表示，依序或`Nothing`如果序列是空的。|  
  
## <a name="in-this-section"></a>本章節內容  
 [如何：存取 XML 子系項目](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 示範如何使用子代 axis 屬性來存取所有的 XML 項目具有指定的名稱的資料，而且包含在指定的 XML 項目。  
  
 [如何：存取 XML 子項目](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 示範如何使用子軸屬性，來存取所有的 XML 項目具有指定的名稱的 XML 子項目。  
  
 [如何：存取 XML 屬性](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 示範如何使用屬性軸屬性，存取所有的 XML 項目具有指定的名稱的 XML 屬性。  
  
 [如何：宣告和使用 XML 命名空間前置詞](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 示範如何宣告 XML 命名空間前置詞，並用來建立及存取 XML 項目。  
  
## <a name="related-sections"></a>相關章節  
 [XML 軸屬性](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 提供描述各種 XML 存取屬性章節的連結。  
  
 [Visual Basic 中的 LINQ to XML 概觀](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 提供簡介使用[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]在 Visual Basic 中。  
  
 [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 提供 Visual Basic 中使用 XML 常值的簡介。  
  
 [在 Visual Basic 中管理 XML](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 提供有關載入及修改 XML，在 Visual Basic 中的章節連結。  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 提供描述如何使用連結[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]在 Visual Basic 中。
