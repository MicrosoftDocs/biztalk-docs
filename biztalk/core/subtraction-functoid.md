---
title: "Subtraction Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Subtraction functoids"
ms.assetid: 188efc20-0c07-4d32-86af-ec0854d641a5
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Subtraction Functoid
Use the **Subtraction** functoid ( ![](../core/media/mathsubtract.gif "mathsubtract")) to calculate the result of subtracting up to 99 numeric values from another numeric value.  
  
## Input  
 **Parameter 1:** A numeric value from which is to be subtracted the combined values of all of the other specified numeric values.  
  
 **Parameters 2 – 100:** Additional numeric values, the combined value of which is to be subtracted from the value specified by parameter 1.  
  
## Output  
 **Output 1:** A numeric value that is the result of subtracting all subsequent specified numeric values from the numeric value specified by parameter 1.  
  
## Remarks  
 Consider the following example of a result produced by this functoid:  
  
-   Parameter 1, P1, is 20.  
  
-   Parameter 2, P2, is 3.  
  
-   Parameter 3, P3, is 2.  
  
-   Parameter 4, P4, is 4.  
  
-   Parameter 5, P5, is 6.  
  
 P1 – (P2 + P3 + P4 + P5) = Output    or    20 – (3 + 2 + 4 + 6) = 5  
  
## See Also  
 [Mathematical Functoids Reference](../core/mathematical-functoids-reference.md)   
 [Mathematical Functoids](../core/mathematical-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)