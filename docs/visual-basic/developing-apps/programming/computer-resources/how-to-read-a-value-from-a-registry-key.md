---
title: "如何：在 Visual Basic 中讀取登錄機碼的值"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4aa939d7b2d89bd878705ac67f2b6f37838f6ea2
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a>如何：在 Visual Basic 中讀取登錄機碼的值
您可以使用 `My.Computer.Registry` 物件的 `GetValue` 方法來讀取 Windows 登錄中的值。  
  
 如果下列範例中的機碼 "Software\MyApp" 不存在，則會擲回例外狀況。 如果下列範例中的 `ValueName` (也就是 "Name") 不存在，則會傳回 `Nothing`。  
  
 `GetValue` 方法也可用來判斷特定登錄機碼中是否有指定的值。  
  
 當程式碼從 Web 應用程式讀取登錄時，會由 Web 應用程式中所實作的驗證和模擬來決定目前的使用者。  
  
### <a name="to-read-a-value-from-a-registry-key"></a>讀取登錄機碼的值  
  
-   使用 `GetValue` 方法，並指定路徑和名稱來讀取登錄機碼的值。 下列範例會從 `HKEY_CURRENT_USER\Software\MyApp` 讀取 `Name` 值，並顯示於訊息方塊中。  
  
     [!code-vb[VbResourceTasks#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_1.vb)]  
  
 這個程式碼範例也可用為 IntelliSense 程式碼片段。 在程式碼片段選擇器中，它位於 [Windows 作業系統] > [登錄] 中。 如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a>判斷登錄機碼中是否有一個值  
  
-   使用 `GetValue` 方法來擷取此值。 下列程式碼會檢查此值是否存在；如果不存在，則傳回訊息。  
  
     [!code-vb[VbResourceTasks#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_2.vb)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 登錄包含可用來儲存資料的最上層或根目錄機碼。 例如，HKEY_LOCAL_MACHINE 根目錄機碼可用於儲存所有使用者所使用的電腦層級設定，而 HKEY_CURRENT_USER 可用於儲存個別使用者的特定資料。  
  
 以下條件可能會造成例外狀況：  
  
-   機碼的名稱是 `Nothing` (<xref:System.ArgumentNullException>)。  
  
-   使用者沒有讀取登錄機碼的權限 (<xref:System.Security.SecurityException>)。  
  
-   機碼名稱超過 255 個字元的限制 (<xref:System.ArgumentException>)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 若要執行此程序，您的組件需要由 <xref:System.Security.Permissions.RegistryPermission> 類別授與的權限層級。 若在部分信任內容中執行，程序可能會因為權限不足而擲回例外狀況。 同樣地，使用者必須有正確的 ACL，才能建立或寫入設定。 例如，具有程式碼存取安全性權限的本機應用程式，可能不具有作業系統權限。 如需詳細資訊，請參閱[程式碼存取安全性基本概念](../../../../framework/misc/code-access-security-basics.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <xref:Microsoft.Win32.RegistryHive>  
 [讀取和寫入登錄](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
