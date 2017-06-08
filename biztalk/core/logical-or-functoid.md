---
title: "Logical OR Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Logical OR functoids, properties"
  - "Logical OR functoids, about Logical OR functoids"
ms.assetid: 58398fbf-0445-4b49-826c-0339dde69c50
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Logical OR Functoid
Use the **Logical OR** functoid ( ![](../core/media/logicalor.gif "logicalor")) to determine whether any of the specified input parameters evaluate to **True**.  
  
## Input  
 **Parameter 1:** A value that can be evaluated as either **True** or **False**.  
  
 **Parameters 2 – 100:** Values that can be evaluated as either **True** or **False**.  
  
## Output  
 **Output 1:** The Boolean value **True** if any of the specified input parameters evaluate to **True**; the Boolean value **False** otherwise.  
  
## Remarks  
 Input parameter values can be in a variety of data types (string, numeric, or logical), although passing strings to this functoid does not yield a meaningful result. For more information about how the **Logical** functoids handle input parameters of different types, see [Logical Functoids Reference](../core/logical-functoids-reference.md).  
  
## See Also  
 [Logical Functoids Reference](../core/logical-functoids-reference.md)   
 [Logical Functoids](../core/logical-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)