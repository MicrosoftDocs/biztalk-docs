---
title: "Expression Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.orch.shape.expression"
ms.assetid: 6e4403da-8a96-40f3-984d-104276c4d3ef
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Expression Shape
You can use the **Expression** shape to enter any expression you choose in your orchestration. For example, you can make a .NET-based call to run an external program, or manipulate the values of your orchestration variables. It is generally not good practice to use it to perform high-level orchestration logic, which preferably would be visible in the orchestration drawing itself. Your orchestration is easier to understand and maintain if your Expression shapes contain simple and modular expressions.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Expression** property|Specify the expression you want to use.|  
|**Report to Analyst** property|Select **True** if you want to make this shape viewable in the Visual Business Analyst Tool.|  
  
## See Also  
 [How to Use Expression Shape](../core/how-to-use-expression-shape.md)