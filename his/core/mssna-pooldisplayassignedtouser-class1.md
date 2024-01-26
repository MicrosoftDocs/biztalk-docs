---
description: "Learn more about: MsSna_PoolDisplayAssignedToUser Class"
title: "MsSna_PoolDisplayAssignedToUser Class1"
ms.custom: ""
ms.date: "12/12/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
