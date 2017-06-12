---
title: "Call Orchestration Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.orch.shape.call"
ms.assetid: e12af37d-302a-4da5-a2c2-741fc1a4bdf5
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Call Orchestration Shape
The **Call Orchestration** shape invokes another orchestration synchronously; that is, the enclosing orchestration waits for the nested orchestration to finish before continuing.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Called Orchestration** property|Specify the name of the orchestration that the current orchestration will call.|  
|**Identifier** property|Specify a unique identifier for this shape.|  
|**Parameters** property|Specify parameters, such as messages, variables, port references, role links, or correlation sets, to be passed to the called orchestration.|  
|**Report to Analyst** property|Select **True** if you want to make this shape viewable in the Visual Business Analyst Tool.|  
  
## See Also  
 [How to Configure the Call Orchestration Shape](../core/how-to-configure-the-call-orchestration-shape.md)