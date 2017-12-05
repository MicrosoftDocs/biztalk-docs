---
title: "MsSna_Lu3270OnConnection Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55a75487-8fa3-4e46-b147-93be68280975
caps.latest.revision: 4
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
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../core/administration-and-management-programmer-s-guide1.md)