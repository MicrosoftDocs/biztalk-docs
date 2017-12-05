---
title: "WinAPPCUnhookBlockingHook1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ddc5686c-f1e0-491f-8a05-33376678514d
caps.latest.revision: 3
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
 [WinAPPCSetBlockingHook](../HIS2010/winappcsetblockinghook2.md)