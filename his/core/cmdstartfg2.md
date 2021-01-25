---
description: "Learn more about: CMDStartFG"
title: "CMDStartFG2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6ada69bd-720b-4670-b0ab-84050e395b01
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
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
