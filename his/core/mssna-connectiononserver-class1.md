---
title: "MsSna_ConnectionOnServer Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4515a41b-e3ee-4271-9714-cc84445808ae
caps.latest.revision: 4
---
# MsSna_ConnectionOnServer Class
Associates a connection with a server.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_ConnectionOnServer : MsSna_Association  
{  
   MsSna_Connection ref PathToConnection;  
   MsSna_Server ref PathToServer;  
};  
```  
  
## Properties  
 **MsSna_Connection**  
 Data Type: **ref PathToConnection** Qualifiers: **Key** Access Type: Read-Only  
  
 The connection to associate with.  
  
 **MsSna_Server**  
 Data Type: **ref PathToServer** Qualifiers: **Key** Access Type: Read-Only  
  
 The path to associate with.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../core/administration-and-management-programmer-s-guide1.md)