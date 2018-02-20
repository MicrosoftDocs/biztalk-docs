---
title: "WinCPICUnhookBlockingHook2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 71a8bd3b-441f-4992-9d3f-dc0d27083862
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
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
 [WinCPICSetBlockingHook](../core/wincpicsetblockinghook2.md)