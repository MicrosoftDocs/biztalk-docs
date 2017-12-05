---
title: "LUA Synchronous and Asynchronous Verb Completion2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 15d75b51-33ab-44fb-b751-4ef4ce1cc5a3
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# LUA Synchronous and Asynchronous Verb Completion
Logical unit application (LUA) verbs can complete execution either synchronously or asynchronously.  
  
## Synchronous Verb Completion  
 When LUA is able to complete all the processing for a verb as soon as it is issued, the verb has completed synchronously. When this happens, the primary return code is set to a value other than LUA_IN_PROGRESS, and the **lua_flag2.async** bit is set to zero.  
  
 The value of the **lua_flag2.async** bit should be tested, not the primary return code being not equal to LUA_IN_PROGRESS. (For information about these returned parameters, see individual verb descriptions.)  
  
## Asynchronous Verb Completion  
 Some LUA verbs (for example, [RUI_PURGE](../core/rui-purge1.md)) complete quickly after local processing. However, most verbs take some time to complete because they require messages to be sent to and received from the local node or the host application.  
  
 When LUA must wait for information from the remote LU or from the local node before it can complete a verb, the verb completes asynchronously.  
  
 When this happens, the **lua_flag2.async** bit is set to 1. The primary return code is also normally set to LUA_IN_PROGRESS, but this value cannot be relied on. The value of the **lua_flag2.async** bit should be tested. The application can now perform other processing, or wait for notification from LUA that the verb has completed. LUA issues this notification by setting the primary return code to its final value and leaving **lua_flag2.async** set to 1.  
  
 When the verb completes, LUA does the following depending on your environment:  
  
-   For Windows, two types of notification are possible. The LUA application either:  
  
     Issues **WaitForSingleObject** or **WaitForMultipleObject**.  
  
     —or—  
  
     Posts the "WinRUI/WinSLI" notification message to the window handle of the **WinRUI**/**WinSLI** message.  
  
     The event method using **WaitForSingleObject** or **WaitForMultipleObject** is the preferred way to receive asynchronous notification on Windows.  
  
-   In the Windows environment, it notifies the completion of an asynchronous request by posting the "WinRUI/WinSLI" notification message to the window handle of the **WinRUI**/**WinSLI** message. A window handle has been added as the first parameter passed to the [WinRUI](../core/winrui2.md) and [WinSLI](../core/winsli2.md) entry points.