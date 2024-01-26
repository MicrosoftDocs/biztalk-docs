---
description: "Learn more about: Windows APPC Asynchronous Support"
title: "Windows APPC Asynchronous Support2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Windows APPC Asynchronous Support
A program that issues a call and does not regain control until the call completes cannot perform any other operations. This type of operation, referred to as blocking, is not suited to a server application designed to handle multiple requests from many clients. Asynchronous call completion returns the initial call immediately so the application can continue with other processes.  
  
 Host Integration Server uses the `RegisterWindowsMessage` function for asynchronous support for APPC applications. With "WinAsyncAPPC" as the input string, an application passes a window handle by which it can be notified of verb completion. The application then issues the verb. When the verb completes, a message is posted to the window handle that was passed, notifying the application that the verb is complete.  
  
 With the exception of asynchronous [RECEIVE_AND_WAIT](./receive-and-wait2.md), [MC_RECEIVE_AND_WAIT](./mc-receive-and-wait2.md), [RECEIVE_AND_POST](./receive-and-post1.md), and [MC_RECEIVE_AND_POST](./mc-receive-and-post2.md), which can issue certain other verbs while pending, a conversation can have only one incomplete operation at any time.
