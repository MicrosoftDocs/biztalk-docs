---
description: "Learn more about: How Exceptions Are Handled"
title: "How Exceptions Are Handled | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "errors, handlers"
  - "scopes, errors"
  - "errors, scopes"
  - "handlers [adapters], errors"
ms.assetid: 30b88d8a-8737-4700-b856-1b49fdf6b6d0
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How Exceptions Are Handled
When an exception occurs within a scope, each logical thread of execution in the scope is stopped. The runtime engine tries to find an exception handler for the appropriate exception.  
  
 If the exception handler is found that matches the specific type or one of its base types, control passes to that handler and its code runs.  
  
> [!NOTE]
>  The exception type must be derived from **System.Exception**.  
  
 Exception handlers are sequential; that is, they will be checked in order to see if they can handle a particular exception. To work properly, exception handlers must be placed so that those handling more specific types come first, followed by those handling more general types. This is so that you can ensure that an exception of a specific type is handled by the appropriate handler, rather than one designed to handle a base type.  
  
 If the exception handler completes normally, control passes to the surrounding scope. If no exception has been thrown in the surrounding scope, the orchestration continues to run. If the exception handler ends with a throw statement, the original exception is thrown again for the surrounding scope to act upon, unless you specify a different exception that you want to be thrown.  
  
 If no exception handler can be located, the default exception handler will run. The default exception handler for a scope will call the compensations for any nested transactions, and then throw the exception again. If you write your own exception handler, you can choose not to propagate the exception.  
  
## See Also  
 [Exceptions](../core/exceptions.md)
