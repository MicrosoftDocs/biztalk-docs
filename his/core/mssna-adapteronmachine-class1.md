---
title: "MsSna_AdapterOnMachine Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a81ade00-05ea-4be5-99cb-e6a63274d62d
caps.latest.revision: 4
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
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../core/administration-and-management-programmer-s-guide1.md)