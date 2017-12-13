---
title: "WinCPICUnhookBlockingHook1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e1b24dba-94d0-45e3-a1c6-692ba53807fa
caps.latest.revision: 3
---
# WinCPICUnhookBlockingHook
The **WinCPICUnhookBlockingHook** function removes any previous blocking hook that has been installed and reinstalls the default blocking mechanism.  
  
## Syntax  
  
```  
  
BOOL WINAPI WinCPICUnhookBlockingHook(void);  
```  
  
## Return Value  
 The return value specifies the outcome of the function. It is not zero if the default mechanism is successfully reinstalled. The value is zero if the mechanism did not reinstall.  
  
## See Also  
 [WinCPICSetBlockingHook](../HIS2010/wincpicsetblockinghook1.md)