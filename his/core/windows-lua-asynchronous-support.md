---
title: "Windows LUA Asynchronous Support1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 50d4398d-1886-4330-8e4c-dedc494c5263
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Windows LUA Asynchronous Support
Asynchronous verb completion returns immediately from issuing an initial verb (before results have been received) so the application can continue with other processes. A program that issues a verb and does not regain control until the operation completes cannot perform any other operations. This synchronous type of operation, called blocking, is not suited to a server application designed to handle multiple requests from many clients.  
  
 By design, logical unit application (LUA) is asynchronous and uses semaphores for notification messages. Semaphores work well for Windows Server. Windows LUA provides the following functions for issuing the Request Unit Interface (RUI) and Session Level Interface (SLI) verbs:  
  
-   [RUI](../Topic/RUI1.md)  
  
-   [SLI](../Topic/SLI1.md)  
  
-   [WinRUI](../Topic/WinRUI2.md)  
  
-   [WinSLI](../Topic/WinSLI2.md)  
  
 **WinRUI** and **WinSLI** provide asynchronous message notification for all Windows-based RUI and SLI verbs, while **RUI** and **SLI** provide support for event notification. Windows version 3.*x* applications use **WinRUI** and **WinSLI** for asynchronous message notification.  
  
 Asynchronous support allows you to be notified of verb completion based on a window handle. You can register a window handle using the RegisterWindowsMessage function with "WinRUI" or "WinSLI" as the string. You then issue a verb using the WinRUI or WINSLI function and passing a window handle. When the LUA verb conversation completes, a message is posted to the window handle that you passed, notifying you that the verb is complete.  
  
 The only other Windows extension functions required for Windows LUA are for initialization ([WinRUIStartup](../Topic/WinRUIStartup2.md) or [WinSLIStartup](../Topic/WinSLIStartup1.md)) and termination ([WinRUICleanup](../Topic/WinRUICleanup2.md) or [WinSLICleanup](../Topic/WinSLICleanup1.md)) purposes. Depending on your application, other Windows extensions may be useful, but they are not required. A complete description of all Windows LUA verbs, routines, and extensions is provided in [LUA RUI Verbs](../Topic/LUA%20RUI%20Verbs1.md), [LUA SLI Verbs](../Topic/LUA%20SLI%20Verbs1.md), and [LUA Extensions for the Windows Environment](../Topic/LUA%20Extensions%20for%20the%20Windows%20Environment1.md).