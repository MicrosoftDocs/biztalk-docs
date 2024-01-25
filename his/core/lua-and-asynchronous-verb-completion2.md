---
description: "Learn more about: LUA and Asynchronous Verb Completion"
title: "LUA and Asynchronous Verb Completion2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# LUA and Asynchronous Verb Completion
Host Integration Server permits one outstanding Windows SNA asynchronous call per connection and one blocking verb per thread. When the asynchronous verb completes, logical unit application (LUA) does the following for a Windows server system.  
  
 Two types of notification are possible:  
  
-   The preferred type is the event method, in which the LUA application issues **WaitForSingleObject/WaitForMultipleObject**.  
  
-   The application can also post the"WinRUI"/"WinSLI" notification message to the window handle of the **WinRUI/WinSLI** message.
