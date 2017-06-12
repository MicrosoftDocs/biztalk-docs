---
title: "How to Add a Scope Shape4 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "adding, Scope shapes"
  - "Scope shape, adding"
ms.assetid: 4ed56ada-a656-40b1-b34a-0c0803c01216
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add a Scope Shape
Follow these steps to add a **Scope** shape.  
  
### To add a scope shape  
  
1.  Right-click the arrow below the **ReceiveFromIn** port, point to **Insert Shape**, and then click **Scope**.  
  
     In the Scope shape, you set operations that might have a fault.  
  
     For example, add a send, a receive and a send port in an SQLExecute orchestration. In this example, you send a message to SERVER. SERVER gives a response. It runs the rest of the orchestration and returns information back to the OutFile port.  
  
2.  In the Scope shape, set the **Transaction** to **None**.  
  
3.  Right-click inside the Scope shape and select **New Exception Handler**.  
  
     This creates the **Catch Exception** block. If an exception occurs from the back-end, it is caught inside the **Catch Exception** block.  
  
4.  In the **Catch Exception** block, you must add the logic.  
    The most important logic that you must set is the type of error message that you expect to receive.  
  
## See Also  
 [Using BizTalk Server Exception Handling](../core/using-biztalk-server-exception-handling4.md)