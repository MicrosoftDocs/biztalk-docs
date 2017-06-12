---
title: "Logical AND Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Logical AND functoids, properties"
  - "Logical AND functoids, about Logical AND functoids"
ms.assetid: 5fef25b1-8f1f-4056-80d0-02438362da1d
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Logical AND Functoid
Use the **Logical AND** functoid ( ![](../core/media/logicaland.gif "logicaland")) to determine whether all of the specified input parameters evaluate to **True**.  
  
## Input  
 **Parameter 1:** A value that can be evaluated as either **True** or **False**.  
  
 **Parameters 2 – 100:** Values that can be evaluated as either **True** or **False**.  
  
## Output  
 **Output 1:** The Boolean value **True** if all of the specified input parameters evaluate to **True**; the Boolean value **False** otherwise.  
  
## Remarks  
 Input parameter values can be in a variety of data types (string, numeric, or logical), although passing strings to this functoid does not yield a meaningful result. For more information about how the **Logical** functoids handle input parameters of different types, see [Logical Functoids Reference](../core/logical-functoids-reference.md).  
  
## See Also  
 [Logical Functoids Reference](../core/logical-functoids-reference.md)   
 [Logical Functoids](../core/logical-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)