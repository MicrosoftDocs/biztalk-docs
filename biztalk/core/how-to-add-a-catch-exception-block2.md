---
description: "Learn how to add and populate a Catch Exception block to act as an exception handler in the BizTalk ServerOrchestration Designer."
title: "How to Add a Catch Exception Block2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Catch Exception blocks"
  - "exceptions, Catch Exception blocks"
ms.assetid: 7c8b6024-e8dc-4417-83f9-bf4032644b91
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Add and Populate a Catch Exception Block

The **Catch Exception** block represents an exception handler. **Catch Exception** blocks are attached to the end of a **Scope** shape in Orchestration Designer. You can attach as many **Catch Exception** blocks as you need.  
  
 You can set up exception handlers to handle different kinds of exceptions. On each exception handler, you specify an exception type. This must be either an exception or an object derived from the class `System`. If an exception is thrown that matches the specified type in an exception handler, that exception handler will be called.  
  
> [!NOTE]
> To add a Catch Exception block to a Scope shape, the Transaction Type property of the Scope shape must be set to **None** or **Long Running**.  
  
### To add and populate a Catch Exception block  
  
1.  Right-click the **Scope** shape to which you want to add a **Catch Exception** block, and then click **New Exception Handler**.  
  
     A **Catch Exception** block is added to the orchestration immediately following the associated **Scope** shape.  
  
2.  In the **Properties** window, specify the properties.  
  
     The most important property is the **Exception Object Type**; this is the type of message it will catch.  
  
3.  In the **Properties** windows, in the **Exception Object Type** list, select  **General Exception**.  
  
    |Property|Description|  
    |--------------|-----------------|  
    |**Exception Object Name**|Assigns a name to the exception object caught by the exception handler.|  
    |**Exception Object Type**|Determines the object type (derived from System.Exception) that this exception handler will catch.|  
  
4.  Inside the Catch Exception block, add shapes to create the process for handling the exception.  
  
    1.  Right-click below the **CatchException** and point to **Insert Shape**, and then select **Construct Message**.  
  
    2.  Double-click inside **MessageAssignment** to open the Text Editor and enter the Message assignment.  
  
         For example, type `Message_3 = Test`.  
  
## See Also  
 [Completing the Exception Message](../core/completing-the-exception-message4.md)   
 [How to Add a Scope Shape](../core/how-to-add-a-scope-shape4.md)   
 [Using BizTalk Server Exception Handling](../core/using-biztalk-server-exception-handling4.md)
