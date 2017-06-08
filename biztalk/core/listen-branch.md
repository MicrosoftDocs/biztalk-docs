---
title: "Listen Branch | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.orch.branch.listen"
ms.assetid: 76f40f18-8df3-4992-9030-8084ae700683
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Listen Branch
The first branch in a **Listen** shape for which a condition is met (a delay is reached or a message is received) will run, and none of the other branches will run. The first shape within a Listen branch must be either a Delay shape or a Receive shape. You can place any other shape below the initial Receive or Delay shape. You can use an activation receive in a Listen branch, but if one branch contains an activation receive, then all branches must contain activation receives, and no time-out can be used. The activation receive must be the first action in each branch.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Activate** property|If the branch contains a Receive shape, select **True** or **False** to specify whether it is an activation receive.|  
|**Branch Type** property|From the drop-down list, select either Receive or Delay to specify the type of the branch. Different properties will be available to you depending on the branch type.|  
|**Delay** property|Specify a time-out using **System.DateTime** or **System.TimeSpan** in order to create a corresponding delay in your orchestration. For example, if you specify **System.DateTime.UtcNow.AddSeconds (60)**, your orchestration will be idle for sixty seconds before proceeding.|  
|**Filter Expression** property|Specify an expression to test properties on the incoming message to decide whether to process it.|  
|**Initializing Correlation Sets** property|From the drop-down list, select the correlation sets which will be initialized by the values in the sent message.|  
|**Following Correlation Sets** property|From the drop-down list, select already-initialized correlation sets.|  
|**Message** property|If the branch contains a Receive shape, select the message to be received from the drop-down list.|  
|**Operation** property|If the branch contains a Receive shape, select the operation represented by the receive from the drop-down list.|  
|**Report to Analyst** property|Select **True** if you want to make this shape viewable in the Visual Business Analyst Tool.|  
  
## See Also  
 [How to Configure the Listen Shape](../core/how-to-configure-the-listen-shape.md)