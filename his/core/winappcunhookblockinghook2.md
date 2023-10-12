---
description: "Learn more about: WinAPPCUnhookBlockingHook"
title: "WinAPPCUnhookBlockingHook2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
