---
title: "sbputerm1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33e378a6-8010-416f-a470-2b55f3518159
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
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