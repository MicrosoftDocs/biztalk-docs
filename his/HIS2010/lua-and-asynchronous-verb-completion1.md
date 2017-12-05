---
title: "LUA and Asynchronous Verb Completion1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b1e2ddca-a24a-4e6b-9e55-5b7cca219977
caps.latest.revision: 5
---
# LUA and Asynchronous Verb Completion
Host Integration Server permits one outstanding Windows SNA asynchronous call per connection and one blocking verb per thread. When the asynchronous verb completes, logical unit application (LUA) does the following for a Windows server system.  
  
 Two types of notification are possible:  
  
-   The preferred type is the event method, in which the LUA application issues **WaitForSingleObject/WaitForMultipleObject**.  
  
-   The application can also post the"WinRUI"/"WinSLI" notification message to the window handle of the **WinRUI/WinSLI** message.