---
title: "CMDStartFG1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 95754a54-e28b-458b-acd2-caced85b641f
caps.latest.revision: 3
---
# CMDStartFG
The **CMDStartFG** function requests that scheduling of the foreground thread be resumed.  
  
## Syntax  
  
```  
  
USHORT FAR CMDStartFG();    
```  
  
## Return Value  
 0  
 The foreground thread was successfully resumed.  
  
 nonzero  
 The foreground thread could not be resumed.  
  
## Remarks  
 The emulator should issue this call after restoring the screen contents when returning to background operation.