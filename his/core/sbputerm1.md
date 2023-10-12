---
description: "Learn more about: sbputerm"
title: "sbputerm1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# sbputerm
The **sbputerm** function must be called when the application terminates. It frees the DL-BASE and Dynamic Access Module (DMOD) resources used by the application.  
  
 For Win32®, do not call **sbputerm** from an entry point in a detached DLL process because it may cause a deadlock inside the SNADMOD.DLL.  
  
## Syntax  
  
```  
  
VOID sbputerm(  
void  
);      
```
