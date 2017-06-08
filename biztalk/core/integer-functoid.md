---
title: "Integer Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Integer functoids, properties"
  - "Integer functoids, about Integer functoids"
  - "Integer functoids"
ms.assetid: 5ae6d0b3-3cf1-4089-909a-f675281dfeae
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Integer Functoid
Use the **Integer** functoid ( ![](../core/media/mathint.gif "mathint")) to return the integer portion of a numeric input parameter.  
  
## Input  
 **Parameter 1:** A numeric value for which the integer portion is sought.  
  
## Output  
 **Output 1:** An integer value that is the integer portion of the specified real number.  
  
## Remarks  
 This functoid removes the decimal point of a number and any digits to the right of the decimal point. Therefore, it is pointless to call this functoid if you know that the input value can never contain a decimal point.  
  
## See Also  
 [Mathematical Functoids Reference](../core/mathematical-functoids-reference.md)   
 [Mathematical Functoids](../core/mathematical-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)   
 [Round Functoid](../core/round-functoid.md)