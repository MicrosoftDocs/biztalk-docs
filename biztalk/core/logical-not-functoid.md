---
title: "Logical NOT Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a097a6c-88d2-4b5d-8fda-7d4560b4a05a
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Logical NOT Functoid
Use the **Logical NOT** functoid (![Logical NOT functoid](../core/media/logical-not-functoid.gif "logical_not_functoid")) to logically negate the value of the Boolean input parameter.  
  
## Input  
 **Parameter 1:** A value that can be evaluated as either **True** or **False**.  
  
## Output  
 **Output 1:** The Boolean value **True** if the specified input parameter evaluates to **False**; the Boolean value **False** otherwise.  
  
## Remarks  
 The input parameter value can be in a variety of data types (string, numeric, or logical), although passing a string to this functoid does not yield a meaningful result. For more information about how the **Logical** functoids handle input parameters of different types, see [Logical Functoids Reference](../core/logical-functoids-reference.md).  
  
## See Also  
 [Logical Functoids Reference](../core/logical-functoids-reference.md)   
 [Logical Functoids](../core/logical-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)