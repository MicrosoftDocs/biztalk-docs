---
title: "SPasswordChange.ullTimeStamp Field | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc7be835-44ee-4413-be15-ccb4b3422653
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SPasswordChange.ullTimeStamp Field
An integer containing a UTC timestamp in FILETIME format.  
  
## Syntax  
  
```cpp#  
  
public: ULONGLONG ullTimeStamp;  
```  
  
## Remarks  
 If zero, then Enterprise Single Sign-On (ENTSSO) uses the current time.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [SPasswordChange Structure (COM)](../core/spasswordchange-structure-com.md)   
 [SPasswordChange Members](../core/spasswordchange-members.md)   
 [Programming with Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md)