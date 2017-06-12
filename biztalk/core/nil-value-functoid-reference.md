---
title: "Nil Value Functoid Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7ad97ac5-dc72-438e-a9fb-8c88d53284d5
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Nil Value Functoid Reference
The **Nil Value** functoid (![Nil Value functoid](../core/media/advanced-nil-value-functoid.gif "advanced_nil_value_functoid")) sets the value of the destination node to **Nil**.  
  
## Input  
 This functoid must have input parameter(s) between 0 and 1.  
  
> [!NOTE]
>  If the input parameter is specified and evaluated to be “True”, the target node should have the xsi:nil property set to “True”. If no input is specified, the condition is considered to be “True”.  
  
## Output  
 **Output 1:** A **Nil** value.  
  
## See Also  
 [Advanced Functoids Reference](../core/advanced-functoids-reference.md)   
 [Advanced Functoids](../core/advanced-functoids.md)