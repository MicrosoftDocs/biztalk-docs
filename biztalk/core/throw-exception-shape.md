---
title: "Throw Exception Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.orch.shape.exception.throw"
ms.assetid: b51b38c6-162e-4e38-9fc6-73ba639814ca
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Throw Exception Shape
You can explicitly throw exceptions in an orchestration with the **Throw Exception** shape. The run-time engine searches for the nearest exception handler that can handle the exception type. It first searches the current orchestration for an enclosing scope, and then considers in order the associated exception handlers of the scope. If the engine does not find an appropriate handler, it searches any orchestration that called the current orchestration for a scope that encloses the point of the call to the current orchestration.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Exception Object** property|Specify the type of the exception being thrown.|  
|**Report to Analyst** property|Select **True** if you want to make this shape viewable in the Visual Business Analyst Tool.|  
  
## See Also  
 [How to Configure the Throw Exception Shape](../core/how-to-configure-the-throw-exception-shape.md)