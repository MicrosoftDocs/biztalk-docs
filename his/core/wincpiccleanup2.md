---
description: "Learn more about: WinCPICCleanup"
title: "WinCPICCleanup2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# WinCPICCleanup
The **WinCPICCleanup** function terminates and deregisters an application from a Microsoft® Windows® Common Programming Interface for Communications (CPI-C) implementation.  
  
## Syntax  
  
```  
  
BOOL WINAPI WinCPICCleanup(void);  
```  
  
## Return Value  
 The return value specifies whether the deregistration was successful. If the value is not zero, the application was successfully deregistered. The application was not deregistered if a value of zero is returned.  
  
## Remarks  
 Use **WinCPICCleanup** to indicate deregistration of a Windows CPI-C application from a Windows CPI-C implementation.
