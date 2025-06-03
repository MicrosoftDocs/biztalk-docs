---
description: "Learn how to add a Scope shape to the Receive port in BizTalk Server."
title: "How to Add a Scope Shape3"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Add Scope Shapes

Use the following procedure to add a Scope shape.  
  
### To add a Scope Shape  
  
1.  Right-click the arrow below the **Receive** port, point to **Insert Shape**, and then select **Scope**.  
  
     ![Image that shows where to select Scope.](../core/media/siebeladapter-18-exceptionhandling-insertscope.gif "SiebelAdapter_18_ExceptionHandling_InsertScope")  
  
     In the **Scope** shape, you set operations that might have a fault.  
  
     For example, add a send, a receive, and a send port in an SQLExecute orchestration. In this example, you send a message to SERVER. SERVER gives a response. It runs the rest of the orchestration and returns information back to the outFile port.  
  
2.  In the **Scope** shape, set the **Transaction** to **None**.  
  
3.  Right-click inside the **Scope** shape, and select **New Exception Handler**.  
  
     ![Image that shows where to select New Exception Handler.](../core/media/siebeladapter-19-exceptionhandling-newexception.gif "SiebelAdapter_19_ExceptionHandling_NewException")  
  
     This creates the **Catch Exception** block. If an exception occurs from the back-end system, it is caught inside the **Catch Exception** block.  
  
4.  In the **Catch Exception** block, you must add the logic.  
  
     The most important logic that you must set is the type of error message that you expect to receive.  
  
## See Also  
 [Using BizTalk Server Exception Handling](../core/using-biztalk-server-exception-handling1.md)
