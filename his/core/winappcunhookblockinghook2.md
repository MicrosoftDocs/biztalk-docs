---
title: "WinAPPCUnhookBlockingHook2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0677c18b-5a74-4a67-a2bb-26a11bd159e9
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# WinAPPCUnhookBlockingHook
The **WinAPPCUnhookBlockingHook** function removes any previous blocking hook that has been installed and reinstalls the default blocking mechanism.  
  
## Syntax  
  
```  
  
BOOL WINAPI WinAPPCUnhookBlockingHook(  
void  
);  
  
```  
  
## Return Value  
 The return value specifies the outcome of the function. It is nonzero if the default mechanism is successfully reinstalled. The value is zero if the mechanism did not reinstall.  
  
## See Also  
 [WinAPPCSetBlockingHook](../core/winappcsetblockinghook1.md)