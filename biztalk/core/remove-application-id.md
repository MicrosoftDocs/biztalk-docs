---
title: "Remove Application ID | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Remove Application ID functoids"
ms.assetid: 4cdfef07-1b23-4844-ad86-28ddbf9bcf19
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Remove Application ID
Use the **Remove Application ID** functoid (  ![RemoveApplicationID functoid](../core/media/removeapplicationidfunctoid-16x16.gif "RemoveApplicationIDFunctoid_16x16")) to remove an identifier for an application object.  
  
## Input  
 **Parameter 1:** A string of up to 50 characters that identifies the type of the object being referenced.  
  
 **Parameter 2:** A string of up to 50 characters that identifies the application instance.  
  
 **Parameter 3:** A string of up to 50 characters that identifies the common object.  
  
## Output  
 **Output 1:** A string of up to 50 characters that identifies the corresponding application object. If no such object is found, an empty string is returned.  
  
## Remarks  
 If the object type (parameter 1) or the application instance (parameter 2) is not valid, an exception is generated.  
  
## See Also  
 [Database Functoids Reference](../core/database-functoids-reference.md)   
 [Database Functoids](../core/database-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)   
 [Format Message Functoid](../core/format-message-functoid.md)   
 [Get Application Value Functoid](../core/get-application-value-functoid.md)   
 [Get Common ID Functoid](../core/get-common-id-functoid.md)   
 [Get Common Value Functoid](../core/get-common-value-functoid.md)   
 [Set Common ID Functoid](../core/set-common-id-functoid.md)