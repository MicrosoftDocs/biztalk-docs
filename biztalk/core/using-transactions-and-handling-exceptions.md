---
title: "Using Transactions and Handling Exceptions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "transactions, orchestrations"
  - "orchestrations, transactions"
  - "orchestrations, errors"
  - "transactions"
  - "errors, orchestrations"
  - "transactions, BizTalk Server Orchestration Engine"
  - "errors, Scope shape [Orchestration Designer]"
  - "Scope shape [Orchestration Designer], errors"
  - "Scope shape [Orchestration Designer], transactions"
ms.assetid: bb38f5eb-6641-4e7c-8e2a-c474fc739999
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Transactions and Handling Exceptions
When you design an orchestration, you should consider carefully where problems might occur and how best to deal with them. Many orchestrations have several potential points of failure. Problems can arise for any number of other reasons; for example, a server might go down or a message might be badly formatted.  
  
 It is especially important for a long-running or complex orchestration to keep track of its state and to report errors as they occur, so that you can resolve problems accurately and with a minimum of effort. It is equally important for an orchestration to maintain the integrity of a set of closely related actions, so that if part of a transaction takes place but another does not, the entire transaction can be rolled back as though it never occurred.  
  
 BizTalk Orchestration enables you to guarantee the atomicity of work, that is, the integrity of related actions, even when external systems are participating in transactions. It gives you tools to handle errors, to maintain the state of an orchestration, and to fix problems as they occur through transactions, compensation, and exception handling.  
  
 As a framework for transactions and exception handling, Orchestration Designer provides the **Scope** shape. A scope can have a transaction type, a compensation, and any number of exception handlers.  
  
 The steps for setting up a transaction and exception handling are:  
  
-   Create a scope.  
  
-   Identify the kind of transaction you need.  
  
-   Determine what will need to be compensated.  
  
-   Identify potential errors.  
  
-   Add appropriate exception handlers and compensation code.  
  
## Examples of Using Transactions, Exception Handlings, and Compensations  
  
-   [Error Handling (BizTalk Server Samples Folder)](../core/error-handling-biztalk-server-samples-folder.md)  
  
-   [Compensation (BizTalk Server Sample)](../core/compensation-biztalk-server-sample.md)  
  
-   Download the SDK sample "Atomic Transactions with COM+ Serviced Components in Orchestrations" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
-   Download the SDK sample "Using the SQL Adapter with Atomic Transactions in Orchestrations" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
-   Download the SDK sample "Using Long-Running Transactions in Orchestrations" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
-   Download the SDK sample "Exception Handling in Orchestrations" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
## In This Section  
  
-   [Scopes](../core/scopes.md)  
  
-   [How to Configure the Scope Shape](../core/how-to-configure-the-scope-shape.md)  
  
-   [Making Orchestrations Transactional](../core/making-orchestrations-transactional.md)  
  
-   [Exceptions](../core/exceptions.md)  
  
-   [Compensation](../core/compensation.md)  
  
## See Also  
 [Using the BizTalk Messaging Engine](../core/using-the-biztalk-messaging-engine.md)