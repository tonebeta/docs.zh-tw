---
title: "C# 的新功能 - C# 指南"
description: "C# 語言的進化方式"
keywords: "C#, 最新功能, 新功能, Roslyn"
author: BillWagner
ms.author: wiwagn
ms.date: 11/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 77deec51-a14d-46d4-9bb3-faf449477149
ms.openlocfilehash: 719fbe826b0b115b19067dbaf0d04f14e6534890
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="whats-new-in-c"></a>C# 的新功能 #

此頁面提供 C# 語言每個主要版本的新功能藍圖。 下列連結提供每個版本中新增主要功能的詳細資訊。

> [!IMPORTANT]
> C# 語言中的部分功能仰賴「標準程式庫」中的型別和方法。 例外狀況處理便是其中一個例子。 每個 `throw` 陳述式或運算式都會受到檢查，以確保擲回衍生自 <xref:System.Exception> 的物件。 每個 `catch` 也一樣會受到檢查，以確保攔截到衍生自 <xref:System.Exception> 的型別。 每個版本都可能會加入新的需求。 若要在較舊的環境中使用最新的語言功能，可能需要安裝特定的程式庫。 每個特定版本的頁面中會記載這些相依性。 若要知道此相依性的背景，可深入了解[語言和程式庫之間的關係](relationships-between-language-and-library.md)。 


* [C# 7.2](csharp-7-2.md):
    - 此頁面說明 C# 語言中的最新功能。 [Visual Studio 2017 15.5 版](https://www.visualstudio.com/vs/whatsnew/)和 [.NET Core 2.0 SDK](../../core/whats-new/index.md) 目前提供 C# 7.2。

* [C# 7.1](csharp-7-1.md)：
    - 此頁面描述 C# 7.1 中的功能。 [Visual Studio 2017 15.3 版](https://www.visualstudio.com/vs/whatsnew/)和 [.NET Core 2.0 SDK](../../core/whats-new/index.md) 已新增這些功能。

* [C# 7](csharp-7.md)：
    - 此頁面說明 C# 7 中新增的功能。 [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) 和 [.NET Core 1.0](../../core/whats-new/index.md) 及更新版本已新增這些功能
     
* [C# 6](csharp-6.md)：
    - 此頁面說明 C# 6 中新增的功能。 若是 Windows 開發人員，這些功能可在 Visual Studio 2015 中使用。若是在 macOS 和 Linux 上探索 C# 的開發人員，則可在 .NET Core 1.0 中使用。

<!--* [C# Interactive](../interactive/index.md): 
    - This page describes C# Interactive, an interactive Read Eval Print Loop (REPL) that you can use to explore the C# language. You can use it to write code interactively and see it execute immediately, without any compile or build step.
-->
* [跨平台支援](../../core/index.md)：
    - 透過 .NET Core 支援，C# 可在多種平台上執行。 如果您有興趣在 macOS 或是其中一個支援的 Linux 發行版本上嘗試 C#，請深入了解 .NET Core。

<!--
- [.NET Compiler Platform SDK](../roslyn/index.md):
    - The .NET Compiler Platform SDK enables you to write code that performs static analysis on C# code. You can use these APIs to find potential errors, or bad practices, suggest fixes, and even implement those fixes.
-->
  
## <a name="previous-versions"></a>舊版本
以下列出舊版 C# 語言及 Visual Studio .NET 中引入的重要功能。  
  
 * Visual Studio .NET 2013： 
     - 此版 Visual Studio 包括 Bug 修正、效能改進，以及 .NET 編譯器平台 (“Roslyn”) (後來成為 .NET 編譯器平台 SDK<!--Link to ../roslyn/index.md-->) 的技術預覽。

 * C# 5 / Visual Studio .NET 2012： 
     - `Async` / `await`，及[呼叫者資訊](../programming-guide/concepts/caller-information.md)屬性。

 * C# 4 / Visual Studio .NET 2010： 
     - `Dynamic`、[具名引數](../programming-guide/classes-and-structs/named-and-optional-arguments.md)、選擇性參數及泛型[共變數/反變數](../programming-guide/concepts/covariance-contravariance/index.md)。

 * C# 3 / Visual Studio .NET 2008： 
     - 物件和集合初始設定式、Lambda 運算式、擴充方法、匿名類型、自動屬性、區域`var`型別推斷、及 [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md)。

 * C# 2 / Visual Studio .NET 2005： 
     - 匿名方法、泛型、可為 Null 的型別、迭代器/yield、`static` 類別，以及委派的共變數/反變數。

 * C# 1.1 / Visual Studio .NET 2003： 
     - `#line` pragma 和 XML 文件註解。

 * C# 1 / Visual Studio .NET 2002： 
     - [C#](../csharp.md) 的初次發行。   
