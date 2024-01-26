---
description: "Learn more about: SPasswordChange.ullTimeStamp Field"
title: "SPasswordChange.ullTimeStamp Field"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
 [SPasswordChange Structure (COM)](../esso/spasswordchange-structure-com.md)   
 [SPasswordChange Members](../esso/spasswordchange-members.md)   
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)
