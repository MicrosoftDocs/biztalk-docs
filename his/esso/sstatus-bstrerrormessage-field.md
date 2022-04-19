---
description: "Learn more about: SStatus.bstrErrorMessage Field"
title: "SStatus.bstrErrorMessage Field | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 01e729a5-b4da-4eec-af74-acd98e108f89
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
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
 [SStatus Structure (COM)](../esso/sstatus-structure-com.md)   
 [SStatus Members](../esso/sstatus-members.md)   
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)
