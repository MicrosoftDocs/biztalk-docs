---
title: "Start Orchestration Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.orch.shape.start"
ms.assetid: 2c1e9b7f-8797-4225-8d7a-2a427a1ca66e
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Start Orchestration Shape
You use the **Start Orchestration** shape to invoke another orchestration—that is, the flow of control in the invoking orchestration proceeds beyond the invocation, without waiting for the invoked orchestration to finish its work.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Called Orchestration** property|Specify the name of the orchestration that the current orchestration will start.|  
|**Parameters** property|Specify parameters, such as messages, variables, port references, role links, or correlation sets, to be passed to the called orchestration. All parameters are in parameters; you cannot pass out or reference parameters to a started orchestration.|  
|**Report to Analyst** property|Select **True** if you want to make this shape viewable in the Visual Business Analyst Tool.|