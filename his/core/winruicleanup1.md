---
description: "Learn more about: WinRUICleanup"
title: "WinRUICleanup1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 966cc622-2c1e-4a43-a01b-118c5658118e
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# WinRUICleanup
The **WinRUICleanup** function terminates and deregisters an application using Request Unit Interface (RUI) verbs from a Microsoft® Windows® logical unit application (LUA) implementation.  
  
## Syntax  
  
```  
  
BOOL WINAPI WinRUICleanup(void);  
```  
  
## Return Value  
 The return code specifies whether the deregistration was successful. If the value is not zero, the application was successfully deregistered. If the value is zero, the application was not deregistered.  
  
## Remarks  
 Use **WinRUICleanup** to indicate deregistration of a Windows LUA application from a Windows LUA implementation. This function can be used, for example, to free up resources allocated to the specific application.  
  
 If **WinRUICleanup** is called while LUs are in session ([RUI_TERM](../core/rui-term2.md) not issued), the cleanup code should issue an **RUI_TERM** close type ABEND for the application for all open sessions.  
  
## See Also  
 [RUI_TERM](../core/rui-term2.md)   
 [WinRUIStartup](../core/winruistartup1.md)
