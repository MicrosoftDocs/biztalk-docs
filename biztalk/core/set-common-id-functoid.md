---
title: "Set Common ID Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Set Common ID functoids"
ms.assetid: 180d7eda-421a-4ef4-9ed4-832fbc4643ea
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Set Common ID Functoid
Use the **Set Common ID** functoid ( ![](../core/media/setcommonid.gif "setcommonid")) to set and return an identifier for a common object.  
  
## Input  
 **Parameter 1:** A string of up to 50 characters that identifies the type of the object being referenced.  
  
 **Parameter 2:** A string of up to 50 characters that identifies the application instance.  
  
 **Parameter 3:** A string of up to 50 characters that identifies the application object.  
  
 **Parameter 4:** An optional string of up to 50 characters that identifies the common object. An empty string for this parameter is treated the same as the parameter not being specified.  
  
## Output  
 **Output 1:** A string of up to 50 characters that identifies the common object, and that is either the same identifier as the fourth parameter or, when the optional fourth parameter is not specified, an automatically generated string that identifies the common object.  
  
## Remarks  
 If parameter 4, identifying the common object, is not specified, then a unique common identifier is generated and associated with the application identifier.  
  
 Only the first three parameters are required. If either of the first two parameters is not valid, an exception is generated.  
  
 An exception is also generated if either of the following conditions is encountered:  
  
-   The indicated application object already has a common object associated with it.  
  
-   The common object, as indicated by using the optional fourth parameter, is not found.  
  
## See Also  
 [Database Functoids Reference](../core/database-functoids-reference.md)   
 [Database Functoids](../core/database-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)   
 [Format Message Functoid](../core/format-message-functoid.md)   
 [Get Application ID Functoid](../core/get-application-id-functoid.md)   
 [Get Application Value Functoid](../core/get-application-value-functoid.md)   
 [Get Common ID Functoid](../core/get-common-id-functoid.md)   
 [Get Common Value Functoid](../core/get-common-value-functoid.md)