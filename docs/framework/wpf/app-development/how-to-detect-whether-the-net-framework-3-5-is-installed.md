---
title: "如何： 偵測是否已安裝.NET Framework 3.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- verifying whether.NET Framework 3.5 is installed [WPF]
- detecting .NET Framework 3.5 installation [WPF]
- detecting whether.NET Framework 3.5 is installed [WPF]
- determining whether.NET Framework 3.5 is installed [WPF]
ms.assetid: 8556a9d2-1eb8-48ef-919c-5baf22a2a9a2
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3b095b1ba918f0a6cf52afa2d559beb2b8c81bc2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-detect-whether-the-net-framework-35-is-installed"></a>如何： 偵測是否已安裝.NET Framework 3.5
系統管理員可以部署之前[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]應用程式為目標的系統上[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]，必須先確認，[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]執行階段會出現。 本主題提供撰寫的指令碼 HTML/javascript，系統管理員可以用來判斷是否[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]存在於系統上。  
  
> [!NOTE]
>  如需詳細資訊，在上安裝、 部署和偵測[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]，請參閱[安裝.NET Framework 開發人員](../../../../docs/framework/install/guide-for-developers.md)。  
  
## <a name="example"></a>範例  
 當[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]已安裝，MSI 新增 「.NET CLR"和版本號碼的使用者代理字串。 下列範例顯示簡單的 HTML 網頁中內嵌的指令碼。 指令碼搜尋使用者代理字串，以判斷是否[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]已安裝，且在搜尋結果中顯示狀態訊息。  
  
> [!NOTE]
>  此指令碼可供 Internet Explorer。 其他瀏覽器使用者代理字串中，可能不包含.NET CLR 的資訊。  
  
```  
<HTML>  
  <HEAD>  
    <TITLE>Test for the .NET Framework 3.5</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT LANGUAGE="JavaScript">  
    <!--  
    var dotNETRuntimeVersion = "3.5.0.0";  
  
    function window::onload()  
    {  
      if (HasRuntimeVersion(dotNETRuntimeVersion))  
      {  
        result.innerText =   
          "This machine has the correct version of the .NET Framework 3.5."  
      }   
      else  
      {  
        result.innerText =   
          "This machine does not have the correct version of the .NET Framework 3.5." +  
          " The required version is v" + dotNETRuntimeVersion + ".";  
      }  
      result.innerText += "\n\nThis machine's userAgent string is: " +   
        navigator.userAgent + ".";  
    }  
  
    //  
    // Retrieve the version from the user agent string and   
    // compare with the specified version.  
    //  
    function HasRuntimeVersion(versionToCheck)  
    {  
      var userAgentString =   
        navigator.userAgent.match(/.NET CLR [0-9.]+/g);  
  
      if (userAgentString != null)  
      {  
        var i;  
  
        for (i = 0; i < userAgentString.length; ++i)  
        {  
          if (CompareVersions(GetVersion(versionToCheck),   
            GetVersion(userAgentString[i])) <= 0)  
            return true;  
        }  
      }  
  
      return false;  
    }  
  
    //  
    // Extract the numeric part of the version string.  
    //  
    function GetVersion(versionString)  
    {  
      var numericString =   
        versionString.match(/([0-9]+)\.([0-9]+)\.([0-9]+)/i);  
      return numericString.slice(1);  
    }  
  
    //  
    // Compare the 2 version strings by converting them to numeric format.  
    //  
    function CompareVersions(version1, version2)  
    {  
      for (i = 0; i < version1.length; ++i)  
      {  
        var number1 = new Number(version1[i]);  
        var number2 = new Number(version2[i]);  
  
        if (number1 < number2)  
          return -1;  
  
        if (number1 > number2)  
          return 1;  
      }  
  
      return 0;  
    }  
  
    -->  
    </SCRIPT>  
  </HEAD>  
  
  <BODY>  
    <div id="result" />  
  </BODY>  
</HTML>  
```  
  
 如果 「.NET CLR"版本的搜尋成功，則會出現下列類型的狀態訊息：  
  
 `This machine has the correct version of the .NET Framework 3.5.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; .NET CLR 3.5.20726; MS-RTC LM 8).`  
  
 否則，就會出現下列類型的狀態訊息：  
  
 `This machine does not have the correct version of the .NET Framework 3.5. The required version is v3.5.0.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; MS-RTC LM 8).`  
  
## <a name="see-also"></a>請參閱  
 [偵測有無安裝 .NET Framework 3.0](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)
