---
title: "Suspend Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.orch.shape.suspend"
ms.assetid: 76e9ea47-1e32-450a-9532-fa311181567d
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Suspend Shape
You can use the **Suspend** shape to make an orchestration instance stop running until an administrator explicitly intervenes, perhaps to reflect an error condition that requires attention beyond the scope of the orchestration. All of the state information for the orchestration instance is saved, and will be reinstated when the administrator resumes the orchestration instance.  
  
 When an orchestration instance is suspended, an error is raised. You can specify a message string to accompany the error to help the administrator diagnose the situation.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Error Message** property|Specify an error message to use in diagnosing the situation.|  
|**Report to Analyst** property|Select **True** if you want to make this shape viewable in the Visual Business Analyst Tool.|  
  
## See Also  
 [How to Configure the Suspend Shape](../core/how-to-configure-the-suspend-shape.md)