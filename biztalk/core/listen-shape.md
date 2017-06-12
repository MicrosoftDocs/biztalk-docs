---
title: "Listen Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.orch.shape.listen"
ms.assetid: 983a0ed0-b964-4736-afb7-5ba4aff4b75d
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Listen Shape
You use the **Listen** shape to make your orchestration wait for any one of several possible events before proceeding. The first branch for which a condition is met (a delay is reached or a message is received) is followed, and none of the other branches will run. You can add as many branches as you want. The first shape within a **Listen** branch must be either a **Delay** shape or a **Receive** shape. You can place any other shape below the initial **Receive** or **Delay** shape. You can use an activation receive in a **Listen** shape, but if one branch contains an activation receive, then all branches must contain activation receives, and no time-out can be used. The activation receive must be the first action in each branch.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Report to Analyst** property|Select **True** if you want to make this shape viewable in the Visual Business Analyst Tool.|  
  
## See Also  
 [How to Configure the Listen Shape](../core/how-to-configure-the-listen-shape.md)