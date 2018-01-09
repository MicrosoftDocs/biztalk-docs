---
title: "MsSna_Lu3270OnConnection Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6002e765-bf21-4a71-b0a4-83b90f480afc
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MsSna_Lu3270OnConnection Class
Associates a 3270 LU with a connection.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_Lu3270OnConnection : MsSna_Association  
{  
   MsSna_Connection ref PathToConnection;  
   MsSna_Lu3270 ref PathToLu3270;  
};  
```  
  
## Properties  
 **MsSna_Connection**  
 Data Type: **ref PathToConnection** Qualifiers: **Key** Access Type: Read-Only  
  
 The connection to associate with.  
  
 **MsSna_Lu3270**  
 Data Type: **ref PathToLu3270** Qualifiers: **Key** Access Type: Read-Only  
  
 The 3270 LU to associate with.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)