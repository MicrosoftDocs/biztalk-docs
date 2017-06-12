---
title: "Scientific Functoids | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Scientific functoids"
  - "functoid types, Scientific"
ms.assetid: 0311b7dc-1955-45af-b858-681faccc939b
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Scientific Functoids
**Scientific** functoids are used to perform a variety of standard trigonometric, logarithmic, and exponential calculations.  
  
 With the exception of the **Base-Specified Logarithm** and **X^Y** functoids, which each take two input parameters, the **Scientific** functoids all take a single parameter.  
  
 The four trigonometric **Scientific** functoids (**Arc Tangent**, **Cosine**, **Sine**, and **Tangent**) all use radians rather than degrees as the units for their relevant input or output parameters. A radian is a unit of measure of angles, such that there are 2π radians in a circle. It follows that:  
  
-   2π radians equals 360 degrees  
  
-   1 radian = 180/π degrees  
  
-   1 degree = π/180 radians  
  
 If your input or output instance messages use degrees as their unit of measure for angles, you will need to use a **Mathematical** functoid in conjunction with a trigonometric **Scientific** functoid to achieve the correct result.  
  
 The **Scientific** functoids are: [10^n](../core/10-n-functoid.md), [Arc Tangent](../core/arc-tangent-functoid.md), [Base-Specified Logarithm](../core/base-specified-logarithm-functoid.md), [Common Logarithm](../core/common-logarithm-functoid.md), [Cosine](../core/cosine-functoid.md), [Natural Exponential Function](../core/natural-exponential-functoid.md), [Natural Logarithm](../core/natural-logarithm-functoid.md), [Sine](../core/sine-functoid.md), [Tangent](../core/tangent-functoid.md), and [X^Y](../core/x-y-functoid.md).  
  
## See Also  
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)   
 [Scientific Functoids Reference](../core/scientific-functoids-reference.md)