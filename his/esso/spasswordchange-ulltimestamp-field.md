---
title: "SPasswordChange.ullTimeStamp Field | Microsoft Docs"
ms.custom: ""
ms.date: "10/27/2016"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9bcd62ab-de38-402e-a983-25cfe4ec8073
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
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
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../esso/includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [SPasswordChange Structure (COM)](../esso/spasswordchange-structure-com.md)   
 [SPasswordChange Members](../esso/spasswordchange-members.md)   
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)