---
title: "Mathematical Functoids Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Mathmatical functoids, about Mathmatical functoids"
  - "Mathmatical functoids, properties"
  - "functoid types, Mathmatical"
ms.assetid: 4346ed03-172f-4182-9219-8e2e06f88867
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Mathematical Functoids Reference
Use **Mathematical** functoids to perform a variety of basic mathematical operations.  
  
> [!IMPORTANT]
>  Because Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the underlying functionality of the .NET Framework, the results produced by some of the **Mathematical** functoids may vary from the equivalent functoids in earlier versions of BizTalk Server. You should test your maps thoroughly to ensure that you are getting the results you expect.  
  
 When a **Mathematical** functoid determines that one or more of its input parameters is not valid, it cancels the operation and returns an empty string, such that a field in an output instance message is created as "\<FieldName>\</FieldName>" and the string [Size](../core/size-functoid.md) functoid returns zero (0).  
  
 When the input parameter descriptions specify a numeric value, strings that can be interpreted as numbers are also accepted.  
  
 For conceptual information about **Mathematical** functoids, see [Mathematical Functoids](../core/mathematical-functoids.md).  
  
 The following table shows the functoids in the **Mathematical** category.  
  
|Mathematical functoid|Description|  
|---------------------------|-----------------|  
|![](../core/media/mathabs.gif "mathabs") [Absolute Value](../core/absolute-value-functoid.md)|Calculates the absolute value of the specified value.|  
|![](../core/media/mathadd.gif "mathadd") [Addition](../core/addition-functoid.md)|Calculates the sum of the numeric input parameters.|  
|![](../core/media/mathdivide.gif "mathdivide") [Division](../core/division-functoid.md)|Calculates the quotient of the specified dividend and divisor.|  
|![](../core/media/mathint.gif "mathint") [Integer](../core/integer-functoid.md)|Returns the integer portion of a numeric input parameter.|  
|![](../core/media/mathmax.gif "mathmax") [Maximum Value](../core/maximum-value-functoid.md)|Determines the largest value among the numeric input parameters.|  
|![](../core/media/mathmin.gif "mathmin") [Minimum Value](../core/minimum-value-functoid.md)|Determines the smallest value among the numeric input parameters.|  
|![](../core/media/mathmod.gif "mathmod") [Modulo](../core/modulo-functoid.md)|Calculates the remainder of the specified integer division.|  
|![](../core/media/mathmultiply.gif "mathmultiply") [Multiplication](../core/multiplication-functoid.md)|Calculates the product of the numeric input parameters.|  
|![](../core/media/mathround.gif "mathround") [Round](../core/round-functoid.md)|Rounds the specified numeric input parameter to the nearest specified number of decimal places.|  
|![](../core/media/mathsqrt.gif "mathsqrt") [Square Root](../core/square-root-functoid.md)|Calculates the square root of a specified numeric value.|  
|![](../core/media/mathsubtract.gif "mathsubtract") [Subtraction](../core/subtraction-functoid.md)|Calculates the result of subtracting up to 99 numeric values from another numeric value.|  
  
## See Also  
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)