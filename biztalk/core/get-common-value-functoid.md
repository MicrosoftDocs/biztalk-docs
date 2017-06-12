---
title: "Get Common Value Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Get Common Value functoids, about Get Common Value functoids"
  - "Get Common Value functoids, properties"
ms.assetid: 14a33cfa-e27a-41f1-82d1-d074117d8990
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Get Common Value Functoid
Use the **Get Common Value** functoid ( ![](../core/media/getcommonvalue.gif "getcommonvalue")) to retrieve a common value.  
  
## Input  
 **Parameter 1:** A string of up to 50 characters that identifies the type of the object being referenced.  
  
 **Parameter 2:** A string of up to 50 characters that identifies the type of the application.  
  
 **Parameter 3:** A string of up to 50 characters that contains the application value.  
  
## Output  
 **Output 1:** A string of up to 50 characters that contains the corresponding common value. If no such value is found, an empty string is returned.  
  
## Remarks  
 If the object type (parameter 1) or the application type (parameter 2) is not valid, an exception is generated.  
  
## See Also  
 [Database Functoids Reference](../core/database-functoids-reference.md)   
 [Database Functoids](../core/database-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)   
 [Format Message Functoid](../core/format-message-functoid.md)   
 [Get Application ID Functoid](../core/get-application-id-functoid.md)   
 [Get Application Value Functoid](../core/get-application-value-functoid.md)   
 [Get Common ID Functoid](../core/get-common-id-functoid.md)   
 [Set Common ID Functoid](../core/set-common-id-functoid.md)