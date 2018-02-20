---
title: "MsSna_Connection.ExchangePassthroughLus Method2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 39bbe411-74e7-4229-a1d0-4145ac1afda0
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MsSna_Connection.ExchangePassthroughLus Method
Returns a value that determines if two LUs are part of a passthrough connection pair.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
boolean ExchangePassthroughLus  
(  
```  
  
#### Parameters  
 *FirstLu*  
 The first LU.  
  
 *SecondLu*  
 The second LU.  
  
## Return Value  
 **true** if the LUs are part of a passthrough pair; otherwise, **false**.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)