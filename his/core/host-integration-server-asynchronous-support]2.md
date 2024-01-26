---
description: "Learn more about: Host Integration Server Asynchronous Support]"
title: "Host Integration Server Asynchronous Support]2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Host Integration Server Asynchronous Support]
Asynchronous call completion returns the initial call immediately so the application can continue with other processes. An application that issues a call and does not regain control until the operation completes is not able to perform any other operations. This type of operation, referred to as blocking, is not suited to a server application designed to handle multiple requests from many clients.  
  
 Through **RegisterWindowsMessage** with "WinAsyncCSV" as the string, you pass a window handle by which you will be notified of call completion. You then make your call and when it completes, a message is posted to the window handle that you passed, notifying you that the call is complete.
