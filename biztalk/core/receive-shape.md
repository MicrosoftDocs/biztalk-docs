---
title: "Receive Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.orch.shape.receive"
ms.assetid: 60625f7e-6a95-4822-b302-aae2adae7252
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receive Shape
Use the **Receive** shape to receive a message from a port. You can use it to start an orchestration by setting the **Activate** property to **True**, so that a message matching criteria specified in a filter expression will be received and the orchestration instance will execute. You can apply a correlation set to ensure that you correctly receive messages that correspond to a given instance of your orchestration.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Activate** property|Specify whether this is an activation receive by selecting **True** or **False**. If **True**, the **Receive** shape must be the first action in the orchestration. If **False**, your orchestration must be called by another orchestration in order to run. **Note:**  Each orchestration must have at least one **Receive** shape with the **Activate** property set to **True**.|  
|**Filter Expression** property|Specify an expression to test properties on the incoming message to decide whether to process it.|  
|**Initializing Correlation Sets** property|From the drop-down list, select the correlation sets which will be initialized by the values in the sent message.|  
|**Following Correlation Sets** property|From the drop-down list, select already-initialized correlation sets.|  
|**Message** property|From the drop-down list, select the message to be received.|  
|**Operation** property|From the drop-down list, select the operation in which to receive the message.|  
|**Report to Analyst** property|Select **True** if you want to make this shape viewable in the Visual Business Analyst Tool.|  
  
## See Also  
 [How to Configure the Receive Shape](../core/how-to-configure-the-receive-shape.md)