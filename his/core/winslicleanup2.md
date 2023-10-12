---
description: "Learn more about: WinSLICleanup"
title: "WinSLICleanup2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
  
 If **WinSLICleanup** is called while LUs are in session ([SLI_CLOSE](../core/sli-close1.md) not issued), the cleanup code should issue an **SLI_CLOSE** close type ABEND for the application for all open sessions.  
  
## See Also  
 [SLI_CLOSE](../core/sli-close1.md)   
 [WinSLIStartup](../core/winslistartup2.md)
