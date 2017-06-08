---
title: "Cumulative Concatenate Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cumulative Concatenate functoids"
ms.assetid: f04c493c-d150-4f80-aca9-9b77889b6b3f
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Cumulative Concatenate Functoid
Use the **Cumulative Concatenate** functoid ( ![](../core/media/cumulativeconcat.gif "cumulativeconcat")) to concatenate multiple instances of a string value that recurs within corresponding instance messages.  
  
## Input  
 **Parameter 1:** A link from a **Record**, **Field Element**, or **Field Attribute** node that contains a string value for which the accumulated concatenation is sought.  
  
 **Parameter 2:** An optional numeric value that indicates the scope to which the accumulation should be performed. The default value is zero (0), indicating that the accumulation scope is the entire input instance message.  
  
## Output  
 **Output 1:** A string value that is the accumulated concatenation of the specified field or record values over the specified or default scope.  
  
## Remarks  
 For more information about the scoping parameter, see [Cumulative Functoids Reference](../core/cumulative-functoids-reference.md).  
  
## See Also  
 [Cumulative Functoids Reference](../core/cumulative-functoids-reference.md)   
 [Cumulative Functoids](../core/cumulative-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)