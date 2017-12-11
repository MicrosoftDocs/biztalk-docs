---
title: "WinSLICleanup1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 774a53d2-cb49-4897-b4bf-8c15eeacd4ce
caps.latest.revision: 3
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
  
 If **WinSLICleanup** is called while LUs are in session ([SLI_CLOSE](../HIS2010/sli-close2.md) not issued), the cleanup code should issue an **SLI_CLOSE** close type ABEND for the application for all open sessions.  
  
## See Also  
 [SLI_CLOSE](../HIS2010/sli-close2.md)   
 [WinSLIStartup](../HIS2010/winslistartup1.md)