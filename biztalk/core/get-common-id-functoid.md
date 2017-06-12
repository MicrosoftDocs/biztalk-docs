---
title: "Get Common ID Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Get Common ID functoids, about Get Common ID functoids"
  - "Get Common ID functoids, properties"
ms.assetid: d5d30c54-8b77-4623-8171-903b98edb9a1
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Get Common ID Functoid
Use the **Get Common ID** functoid ( ![](../core/media/getcommonid.gif "getcommonid")) to retrieve an identifier for a common object.  
  
## Input  
 **Parameter 1:** A string of up to 50 characters that identifies the type of the object being referenced.  
  
 **Parameter 2:** A string of up to 50 characters that identifies the application instance.  
  
 **Parameter 3:** A string of up to 50 characters that identifies the application object.  
  
## Output  
 **Output 1:** A string of up to 50 characters that identifies the corresponding common object. If no such object is found, an empty string is returned.  
  
## Remarks  
 If the object type (parameter 1) or the application instance (parameter 2) is not valid, an exception is generated.  
  
## See Also  
 [Database Functoids Reference](../core/database-functoids-reference.md)   
 [Database Functoids](../core/database-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)   
 [Format Message Functoid](../core/format-message-functoid.md)   
 [Get Application ID Functoid](../core/get-application-id-functoid.md)   
 [Get Application Value Functoid](../core/get-application-value-functoid.md)   
 [Get Common Value Functoid](../core/get-common-value-functoid.md)   
 [Set Common ID Functoid](../core/set-common-id-functoid.md)