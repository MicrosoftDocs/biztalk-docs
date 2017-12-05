---
title: "Windows APPC Asynchronous Support1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3abf5f1-8f71-40d8-acbe-25251700f38f
caps.latest.revision: 3
---
# Windows APPC Asynchronous Support
A program that issues a call and does not regain control until the call completes cannot perform any other operations. This type of operation, referred to as blocking, is not suited to a server application designed to handle multiple requests from many clients. Asynchronous call completion returns the initial call immediately so the application can continue with other processes.  
  
 [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] uses the `RegisterWindowsMessage` function for asynchronous support for APPC applications. With "WinAsyncAPPC" as the input string, an application passes a window handle by which it can be notified of verb completion. The application then issues the verb. When the verb completes, a message is posted to the window handle that was passed, notifying the application that the verb is complete.  
  
 With the exception of asynchronous [RECEIVE_AND_WAIT](../HIS2010/receive-and-wait1.md), [MC_RECEIVE_AND_WAIT](../HIS2010/mc-receive-and-wait1.md), [RECEIVE_AND_POST](../HIS2010/receive-and-post2.md), and [MC_RECEIVE_AND_POST](../HIS2010/mc-receive-and-post1.md), which can issue certain other verbs while pending, a conversation can have only one incomplete operation at any time.