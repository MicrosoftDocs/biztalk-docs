---
title: "sbputerm2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e48cf5b-97b0-4820-ba56-dd3951503c6c
caps.latest.revision: 3
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