---
title: "Exception Handling in the Business Process Management Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "errors, tutorials"
  - "process management solution tutorial, errors"
ms.assetid: ac9fcb33-7dac-448e-88b8-04d4d439ea6a
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Exception Handling in the Business Process Management Solution
The business process management solution uses a special exception handling orchestration, as well as the standard BizTalk Server exception handling, and for adapter, pipeline, mapping, and routing failures, the new error reporting feature. This customized system is built around the **ExceptionHandler** orchestration. The solution uses the **ExceptionHandler** orchestration to retry an operation or to retry a call that might succeed after a transient problem.  
  
> [!NOTE]
>  You can re-use code from orchestrations, such as **Activate**, that use the **ExceptionHandler** orchestration. All of these orchestrations include a scope titled **CallingCode** with an attached **Exception** block. Replace the code in the **CallingCode** scope with your code. The **Exception** block defines all of the variables need to call the **ExceptionHandler** orchestration. Edit the values assigned to the variables.  
  
 The solution uses custom exceptions, and a couple pre-defined BizTalk exceptions, for cases where the error is unrecoverable such as a malformed order message.  
  
> [!NOTE]
>  The solution uses a custom adapter for handling failures on some ports. For more information about the adapter, see [The Ops Adapter](../core/the-ops-adapter.md).  
  
 This section describes the **ExceptionHandler** orchestration and the custom exceptions. It also discusses, briefly, how the solution employs the error reporting product feature.  
  
## In This Section  
  
-   [The ExceptionHandler Orchestration](../core/the-exceptionhandler-orchestration.md)  
  
-   [Custom Exceptions](../core/custom-exceptions.md)