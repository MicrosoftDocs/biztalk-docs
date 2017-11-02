---
title: "WinSLICleanup2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1f1f4abe-da1d-47c7-a2e6-d5a21ca860de
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# WinSLICleanup
The **WinSLICleanup** function terminates and deregisters an application using Session Level Interface (SLI) verbs from a Microsoft® Windows® logical unit application (LUA) implementation.  
  
## Syntax  
  
```  
  
BOOL WINAPI WinSLICleanup(void);  
```  
  
## Return Value  
 The return code specifies whether the deregistration was successful. If the value is not zero, the application was successfully deregistered. If the value is zero, the application was not deregistered.  
  
## Remarks  
 Use **WinSLICleanup** to indicate deregistration of a Windows LUA application from a Windows LUA implementation. This function can be used, for example, to free up resources allocated to the specific application.  
  
 If **WinSLICleanup** is called while LUs are in session ([SLI_CLOSE](../core/sli-close.md) not issued), the cleanup code should issue an **SLI_CLOSE** close type ABEND for the application for all open sessions.  
  
## See Also  
 [SLI_CLOSE](../core/sli-close.md)   
 [WinSLIStartup](../core/winslistartup.md)