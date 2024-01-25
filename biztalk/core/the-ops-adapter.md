---
description: "Learn more about: The Ops Adapter"
title: "The Ops Adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The Ops Adapter
The design of the solution is to pass, where possible, problematic messages and errors to operations systems that make a decision about fixing the error or terminating the order. The Ops adapter, combined with the new error reporting feature, handles many of these cases.  
  
 The solution uses the adapter on a port configured to use the new error reporting feature. When it receives an error, the adapter calls two methods, **Initialize** and **Execute**, on a class in a specified assembly. In the solution, these methods send the error to the correct operations group.  
  
 The solution includes a sample handler, although you can easily write your own and use the adapter in other solutions. For general information about the new error reporting feature, see [Using Failed Message Routing](../core/using-failed-message-routing.md).  
  
> [!NOTE]
>  The Ops adapter is built using the Adapter Framework. For information about building adapters with the framework, see [Developing Custom Adapters](../core/developing-custom-adapters.md).  
  
 This section describes how the adapter works and how to configure it, and provides details about the error handler assemblies. The section concludes with implementation details that would be helpful to users who wish to modify the adapter or use it in other applications.  
  
## In This Section  
  
-   [Using the Ops Adapter](../core/using-the-ops-adapter.md)  
  
-   [The Sample Operations Error Handler](../core/the-sample-operations-error-handler.md)  
  
-   [Ops Adapter Implementation Details](../core/ops-adapter-implementation-details.md)
