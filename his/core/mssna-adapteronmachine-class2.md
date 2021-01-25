---
description: "Learn more about: MsSna_AdapterOnMachine Class"
title: "MsSna_AdapterOnMachine Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8dec2460-da39-4c09-ac66-4730701881ad
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
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
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
