---
title: "SStatus.bstrErrorMessage Field | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 65b4d7b7-6482-428e-ad40-e33bcb29d61c
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SStatus.bstrErrorMessage Field
A string that contains an error message.  
  
## Syntax  
  
```cpp#  
  
public: BSTR bstrErrorMessage;  
```  
  
## Remarks  
 **bstrErrorMessage** Can be NULL. You must free **bstrEerrorMessage** after every use.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [SStatus Structure (COM)](../core/sstatus-structure-com.md)   
 [SStatus Members](../core/sstatus-members.md)   
 [Programming with Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md)