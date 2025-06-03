---
description: "Learn more about: MsSna_AdapterOnMachine Class"
title: "MsSna_AdapterOnMachine Class2"
ms.custom: ""
ms.date: "12/12/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: reference
---
# MsSna_AdapterOnMachine Class
Associates an adapter with a computer.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_AdapterOnMachine : MsSna_Association  
{  
   MsSna_Adapter ref PathToAdapter;  
   MsSna_Server ref PathToServer;  
};  
```  
  
## Properties  
 **MsSna_Adapter**  
 Data Type: **ref PathToAdapter** Qualifiers: **Key** Access Type: Read-Only  
  
 The adapter to associate with.  
  
 **MsSna_Server**  
 Data Type: **ref PathToServer** Qualifiers: **Key** Access Type: Read-Only  
  
 The server to associate with.  
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10 
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
