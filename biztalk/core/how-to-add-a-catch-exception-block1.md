---
description: "Learn how to add a Catch Exception block to set up an exception handler in the BizTalk Server Orchestration Designer."
title: "How to Add a Catch Exception Block1"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Add a Catch Exception Block

The **Catch Exception** block represents an exception handler. **Catch Exception** blocks are attached to the end of a **Scope** shape in Orchestration Designer. You can attach as many **Catch Exception** blocks as you need.  
  
 You can set up exception handlers to handle different kinds of exceptions. On each exception handler, you specify an exception type, which must be either an exception or an object derived from the class `System`. If an exception is thrown that matches the specified type in an exception handler, that exception handler will be called.  
  
> [!NOTE]
> To add a **Catch Exception** block to a **Scope** shape, the Transaction Type property of the **Scope** shape must be set to **None** or **Long Running**.  
  
### To add and populate a Catch Exception block  
  
1.  Right-click the **Scope** shape to which you want to add a **Catch Exception** block, and then click **New Exception Handler**.  
  
     A **Catch Exception** block is added to the orchestration immediately following the associated **Scope** shape.  
  
2.  In the **Properties** window, specify the properties.  
  
     The most important property is the Exception Object Type; this is the type of message it will catch.  
  
    |Property|Description|  
    |--------------|-----------------|  
    |Exception Object Name|Assigns a name to the exception object caught by the exception handler.|  
    |Exception Object Type|Determines the object type (derived from System.Exception) that this exception handler will catch.|  
  
3.  In the **Properties** window, in the **Exception Object Type** list, select the **General Exception**.  
  
4.  Inside the **Catch Exception** block, add shapes to create the process for handling the exception.  
  
5.  Right-click below the **Catch Exception** block, point to **Insert Shape**, and then select **Construct Message**.  
  
6.  Double-click inside **MessageAssignment** to activate the Text Editor and enter the Message assignment.  
  
     For example, type `Message_3 = Test`.  
  
## See Also  
 [Completing the Exception Message](../core/completing-the-exception-message5.md)   
 [How to Add a Scope Shape](../core/how-to-add-a-scope-shape2.md)   
 [Using BizTalk Server Exception Handling](../core/using-biztalk-server-exception-handling3.md)
