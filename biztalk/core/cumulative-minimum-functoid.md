---
title: "Cumulative Minimum Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cumulative Minimum functoids"
ms.assetid: 0dc39b45-0928-4fe9-a56f-f2d58665f81b
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Cumulative Minimum Functoid
Use the **Cumulative Minimum** functoid ( ![](../core/media/cumulativemin.gif "cumulativemin")) to determine the minimum value of a numeric value that recurs within corresponding instance messages.  
  
## Input  
 **Parameter 1:** A link from a **Record**, **Field Element**, or **Field Attribute** node that contains a numeric value for which the minimum instance is sought.  
  
 **Parameter 2:** An optional numeric value that indicates the scope to which the accumulation should be performed. The default value is zero (0), indicating that the accumulation scope is the entire instance message.  
  
## Output  
 **Output 1:** A numeric value that is the minimum value of the specified field or record values over the specified or default scope.  
  
## Remarks  
 For more information about the scoping parameter, see [Cumulative Functoids Reference](../core/cumulative-functoids-reference.md).  
  
## See Also  
 [Cumulative Functoids Reference](../core/cumulative-functoids-reference.md)   
 [Cumulative Functoids](../core/cumulative-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)