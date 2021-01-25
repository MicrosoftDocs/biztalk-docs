---
description: "Learn more about: What Is an Adapter Handler?"
title: "What Is an Adapter Handler? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "handlers [adapters]"
  - "adapters, handlers"
  - "handlers [adapters], about handlers"
ms.assetid: 4d1afa39-6320-467f-a7e8-f5f18236648e
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Is an Adapter Handler?
An adapter handler is an instance of a BizTalk host in which the adapter code runs. When you specify a send or receive handler for an adapter you are specifying which host instance the adapter code will run in the context of. An adapter handler is responsible for executing the adapter and contains properties for a specific instance of an adapter. A default BizTalk Server configuration will create adapter handlers for all of the installed adapters, but you may want to create additional adapter handlers for purposes of load balancing or to provide process isolation for a particular adapter handler.  
  
 Adapter handlers are bound to a BizTalk Host instance, and BizTalk Host instances are bound to a BizTalk server. Therefore, you must add additional BizTalk servers to your BizTalk group if you want to load balance adapter processing across BizTalk servers. You do not need to add additional BizTalk servers to your BizTalk group if you are creating additional adapter handlers for the purpose of process isolation.  
  
 If you need to create a new host instance to run an adapter handler in, you must first create a host and then create an instance of that host to run on one of your BizTalk servers. For more information, see [How to Create a New Host](../core/how-to-create-a-new-host.md) and [How to Add a Host Instance](../core/how-to-add-a-host-instance.md).  
  
 All adapter handlers except for HTTP and SOAP adapter receive handlers must be configured to run in an in-process host. HTTP and SOAP adapter receive handlers can only be run in an isolated host.  
  
## See Also  
 [Creating and Deleting Adapter Handlers](../core/creating-and-deleting-adapter-handlers.md)
