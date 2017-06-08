---
title: "Round Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Round functoids"
ms.assetid: a0993b70-e388-470f-bbe7-b40f61595486
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Round Functoid
Use the **Round** functoid ( ![](../core/media/mathround.gif "mathround")) to round the specified numeric input parameter to the nearest specified number of decimal places.  
  
## Input  
 **Parameter 1:** A numeric value to be rounded to the nearest number of decimal places, as specified by parameter 2.  
  
 **Parameter 2:** A numeric value that is a (presumably small) whole number representing the number of decimal places to which the number specified by parameter 1 will be rounded.  
  
## Output  
 **Output 1:** A numeric value that is the result of rounding the number specified by parameter 1 to the number of decimal places specified by parameter 2.  
  
## Remarks  
 If parameter 2 is zero (0) or not provided, the result is a whole number.  
  
 This functoid uses banker or even rounding. For example, if the second parameter is 0 for whole number rounding, then 1.5 rounds to 2, while 4.5 rounds to 4.  
  
## See Also  
 [Mathematical Functoids Reference](../core/mathematical-functoids-reference.md)   
 [Mathematical Functoids](../core/mathematical-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)   
 [Integer Functoid](../core/integer-functoid.md)