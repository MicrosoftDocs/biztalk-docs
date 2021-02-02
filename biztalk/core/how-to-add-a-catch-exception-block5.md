---
description: "Learn more about: How to Add a Catch Exception Block"
title: "How to Add a Catch Exception Block5 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "exceptions, adding Catch Exception block"
  - "Catch Exception blocks, adding"
ms.assetid: 4875060c-976c-40e7-830a-ffd1a47ba68a
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add a Catch Exception Block
To add a **Catch Exception** block to a **Scope** shape, the **Transaction Type** property of the **Scope** shape must be set to **None** or **Long Running**.  
  
### To add a catch exception block  
  
1.  Right-click the **Scope** shape, and then click **New Exception Handler**.  
  
     A **Catch Exception** block is added to the orchestration immediately following the associated **Scope** shape.  
  
2.  In the **Properties** window, specify the properties.  
  
     The most important property is the **Exception Object Type**; this is the type of message it will catch.  
  
    |Property|Description|  
    |--------------|-----------------|  
    |**Exception Object Name**|Assigns a name to the exception object caught by the exception handler.|  
    |**Exception Object Type**|Determines the object type (derived from System.Exception) that this exception handler will catch.|  
  
3.  In the **Properties** window, in the **Exception Object Type** list, select **General Exception**.  
  
4.  Inside the **Catch Exception** block, add shapes to create the process for handling the exception.  
  
    1.  Right-click below the **CatchException** and point to **Insert Shape**, and then select **Construct Message**.  
  
    2.  Double-click inside **MessageAssignment** to open the Text Editor and enter the Message assignment.  
  
         For example, type `Message_3 = Test`.  
  
## See Also  
 [Completing the Exception Message](../core/completing-the-exception-message1.md)   
 [How to Add a Scope Shape](../core/how-to-add-a-scope-shape5.md)   
 [Using BizTalk Server Exception Handling](../core/using-biztalk-server-exception-handling5.md)
