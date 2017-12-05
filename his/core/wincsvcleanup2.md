---
title: "WinCSVCleanup2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2e228bc9-68a9-4a95-ac48-02f512919cfe
caps.latest.revision: 3
---
# WinCSVCleanup
The **WinCSVCleanup** function terminates and deregisters an application from a Windows® CSV implementation.  
  
## Syntax  
  
```  
  
BOOL WINAPI WinCSVCleanup(void);  
```  
  
## Return Value  
 The return value specifies whether the deregistration was successful. If the value is nonzero, the application was successfully deregistered. The application was not deregistered if a value of zero is returned.  
  
## Remarks  
 Use **WinCSVCleanup** to indicate deregistration of a Windows CSV application from a Windows CSV implementation. This function can be used, for example, to free up resources allocated to the specific application.