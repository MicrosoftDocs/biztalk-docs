---
description: "Learn how to add a Scope shape that contains a CatchException block to the ReceiveFromIn port in BizTalk Server."
title: "How to Add a Scope Shape5"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Add a Scope Shape

Follow these steps to add a **Scope**shape.  
  
### To add a Scope shape  
  
1.  Right-click the arrow below the **ReceiveFromIn** port, point to **Insert Shape**, and then click **Scope**.  
  
     In the **Scope** shape, you set operations that might have a fault.  
  
     For example, add a send, a receive and a send port in an SQLExecute orchestration. In this example, you send a message to SERVER. SERVER gives a response. It runs the rest of the orchestration and returns information back to the OutFile port.  
  
2.  In the **Scope** shape, set the **Transaction Type** to **None**.  
  
3.  Right-click inside the **Scope** shape and select **New Exception Handler**.  
  
     This creates the `Catch Exception`block. If an exception occurs from the back-end, it is caught inside the `Catch Exception`block.  
  
4.  In the `Catch Exception` block, you must add the logic.  
  
     The most important logic that you must set is the type of error message that you expect to receive.  
  
## See Also  
 [Using BizTalk Server Exception Handling](../core/using-biztalk-server-exception-handling5.md)
