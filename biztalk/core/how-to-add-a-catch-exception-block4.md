---
description: "Learn more about: How to Add a Catch Exception Block"
title: "How to Add a Catch Exception Block4 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Catch Exception blocks, adding"
  - "exception handling, Catch Exception blocks"
ms.assetid: 632fa089-a1af-4126-b32b-68d4d8942387
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adding a Catch Exception Block
The **Catch Exception** block represents an exception handler. **Catch Exception** blocks are attached to the end of a **Scope** shape in Orchestration Designer. You can attach as many **Catch Exception** blocks as you need.  
  
 You can set up exception handlers to handle different kinds of exceptions. On each exception handler, you specify an exception type, which must be either an exception or an object derived from the class System. If an exception is thrown that matches the specified type in an exception handler, that exception handler is called.  
  
> [!NOTE]
>  To add a **Catch Exception** block to a **Scope** shape, the Transaction Type property of the **Scope** shape must be set to **None** or **Long Running**.  
  
|Adding and populating a Catch Exception block|  
|---------------------------------------------------|  
|1.  Right-click the **Scope** shape that you want to add a **Catch Exception** block to, and click **New Exception Handler**.<br />     A **Catch Exception** block is added to the orchestration immediately following the associated **Scope** shape.<br />2.  In the **Properties** window, specify the properties. The most important is the **Exception Object Type**; this is the type of message it will catch.<br />     **Exception Object Name**<br />     - Assigns a name to the exception object caught by the exception handler.<br />     **Exception Object Type**<br />     - Determines the object type (derived from System.Exception) that this exception handler will catch.<br />3.  In the **Properties** window, open the **Exception Object Type** list. This list contains the **General Exception**.<br />4.  Inside the **Catch Exception** block, add shapes to create the process for handling the exception.<br />5.  Right-click below the **Catch Exception**, point to **Insert Shape**, and select **Construct Message**.<br />6.  Double-click inside **MessageAssignment** to activate the Text Editor, and enter the Message assignment.<br />     For example, type in Message_3 = Test.<br />     ![Screenshot that shows the BizTalk Expression Editor.](../core/media/siebeladapter-21-exceptionhandling-message3test.gif "SiebelAdapter_21_ExceptionHandling_Message3Test")|  
  
## See Also  
 [Completing the Exception Message](../core/completing-the-exception-message2.md)   
 [How to Add a Scope Shape](../core/how-to-add-a-scope-shape3.md)   
 [Using BizTalk Server Exception Handling](../core/using-biztalk-server-exception-handling1.md)
