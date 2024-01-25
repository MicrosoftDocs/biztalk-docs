---
description: "Learn more about: CMDStartFG"
title: "CMDStartFG2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
