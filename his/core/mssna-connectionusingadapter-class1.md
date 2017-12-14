---
title: "MsSna_ConnectionUsingAdapter Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9be6e0e1-de26-40a9-90cf-ce3bcac0a1eb
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MsSna_ConnectionUsingAdapter Class
Associates a connection with an adapter.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_ConnectionUsingAdapter : MsSna_Association   
{  
   MsSna_Adapter ref PathToAdapter;  
   MsSna_Connection ref PathToConnection;  
};  
```  
  
## Properties  
 **MsSna_Adapter**  
 Data Type: **ref PathToAdapter** Qualifiers: **Key** Access Type: Read-Only  
  
 The adapter to associate with.  
  
 **MsSna_Connection**  
 Data Type: **ref PathToConnection** Qualifiers: **Key** Access Type: Read-Only  
  
 The connection to associate with.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)