---
title: "MsSna_PoolOnServer Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 91735700-a1d5-47f5-a437-9d67625c48ab
caps.latest.revision: 4
---
# MsSna_PoolOnServer Class
Associates a pool with a server.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_PoolOnServer : MsSna_Association   
{  
   MsSna_Pool ref PathToPool3270;  
   MsSna_Server ref PathToServer;  
};  
```  
  
## Properties  
 **MsSna_Pool**  
 Data Type: ref PathToPool3270 Qualifiers: **Key** Access Type: Read-Only  
  
 The pool to associate with.  
  
 **MsSna_Server**  
 Data Type: **ref PathToServer** Qualifiers: **Key** Access Type: Read-Only  
  
 The server to associate with.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../core/administration-and-management-programmer-s-guide1.md)