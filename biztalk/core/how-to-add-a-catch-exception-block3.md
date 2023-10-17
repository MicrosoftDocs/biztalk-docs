---
description: "Learn how to add and populate a Catch Exception block and attach it to the end of a Scope shape in the BizTalk Server Orchestration Designer."
title: "How to Add a Catch Exception Block3 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Scope shape [Orchestration Designer], Catch Exception block [Orchestration Designer]"
  - "Catch Exception block [Orchestration Designer]"
  - "Catch Exception block [Orchestration Designer], creating"
  - "Catch Exception block [Orchestration Designer], exception handler"
  - "Catch Exception block [Orchestration Designer], about Catch Exception blocks"
  - "Orchestration Designer, errors"
ms.assetid: 63ca4a60-b657-452a-86fd-78968ccf2933
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add and Populate a Catch Exception Block

The **Catch Exception** block represents an exception handler. **Catch Exception** blocks are attached to the end of a **Scope** shape in Orchestration Designer. You can attach as many **Catch Exception** blocks as you need.  
  
 You can set up exception handlers to handle different kinds of exceptions. On each exception handler, you specify an exception type, which must be either a fault message or an object derived from the class **System.Exception**. If you do not specify an exception type, the exception block will be treated as a general exception handler, and can catch exceptions that do not derive from **System.Exception**.  
  
 If an exception is thrown that matches the specified type in an exception handler, that exception handler will be called. If some other exception is thrown, it will be handled by the default exception handler.  
  
> [!NOTE]
> To add a **Catch Exception** block to a **Scope** shape, the **Transaction Type** property of the **Scope** shape must be set to **None** or **Long Running**.  
  
### To add a Catch Exception block  
  
1.  Right-click the **Scope** shape to which you want to add a **Catch Exception** block, and then click **New Exception Handler**.  
  
     A **Catch Exception** block is added to the orchestration immediately following the associated **Scope** shape.  
  
2.  In the Properties window, specify the following properties:  
  
    |Property|Description|  
    |--------------|-----------------|  
    |Exception Object Name|Assigns a name to the exception object caught by the exception handler.|  
    |Exception Object Type|Determines the object type (derived from System.Exception) that this exception handler will catch.|  
  
3.  Inside the **Catch Exception** block, add shapes to create the process for handling the exception.  
  
> [!NOTE]
> If you specify General Exception as the **Exception** object type, the **Catch Exception** block will intercept any exception, including those that are not derived from **System.Exception**. In such a case, you will not have access to an exception object. Within this block, if you use a **Throw Exception** shape with the General Exception type, you will be effectively rethrowing the caught exception.  
  
## See Also  
 [Exceptions](../core/exceptions.md)
