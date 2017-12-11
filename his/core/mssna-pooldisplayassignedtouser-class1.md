---
title: "MsSna_PoolDisplayAssignedToUser Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 274ae97c-3b3f-40f9-90e9-b7954aa055b9
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MsSna_PoolDisplayAssignedToUser Class
Associates a display pool with a user.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_PoolDisplayAssignedToUser : MsSna_PoolAssignedToUser  
{  
   MsSna_PoolDisplay ref PathToPoolDisplay;  
   MsSna_ConfiguredUser ref PathToUser;  
};  
```  
  
## Properties  
 **MsSna_PoolDisplay**  
 Data Type: **ref PathToPoolDisplay** Qualifiers: **Key** Access Type: Read-Only  
  
 The display pool to associate with.  
  
 **MsSna_ConfiguredUser**  
 Data Type: **ref PathToUser** Qualifiers: **Key** Access Type: Read-Only  
  
 The user to associate with.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](../HIS2010/administration-and-management-programmer-s-guide1.md)