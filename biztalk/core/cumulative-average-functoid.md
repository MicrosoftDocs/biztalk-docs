---
title: "Cumulative Average Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cumulative Average functoids"
ms.assetid: b8ed38e8-6674-40c1-af26-26ab79bc3a81
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Cumulative Average Functoid
Use the **Cumulative Average** functoid ( ![](../core/media/cumulativeavg.gif "cumulativeavg")) to calculate the accumulated average of a numeric value that recurs within corresponding instance messages.  
  
## Input  
 **Parameter 1:** A link from a **Record**, **Field Element**, or **Field Attribute** node that contains a numeric value for which the accumulated average is sought.  
  
 **Parameter 2:** An optional numeric value that indicates the scope to which the accumulation should be performed. The default value is zero (0), indicating that the accumulation scope is the entire input instance message.  
  
## Output  
 **Output 1:** A numeric value that is the accumulated average value of the specified field or record values over the specified or default scope.  
  
## Remarks  
 For more information about the scoping parameter, see [Cumulative Functoids Reference](../core/cumulative-functoids-reference.md).  
  
## See Also  
 [Cumulative Functoids Reference](../core/cumulative-functoids-reference.md)   
 [Cumulative Functoids](../core/cumulative-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)