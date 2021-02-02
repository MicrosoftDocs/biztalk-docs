---
description: "Learn more about: LUA and Asynchronous Verb Completion"
title: "LUA and Asynchronous Verb Completion2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55daa571-7f93-46d3-9fca-ed3ab542c56b
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# LUA and Asynchronous Verb Completion
Host Integration Server permits one outstanding Windows SNA asynchronous call per connection and one blocking verb per thread. When the asynchronous verb completes, logical unit application (LUA) does the following for a Windows server system.  
  
 Two types of notification are possible:  
  
-   The preferred type is the event method, in which the LUA application issues **WaitForSingleObject/WaitForMultipleObject**.  
  
-   The application can also post the"WinRUI"/"WinSLI" notification message to the window handle of the **WinRUI/WinSLI** message.
