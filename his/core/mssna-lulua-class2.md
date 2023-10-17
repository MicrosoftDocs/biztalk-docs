---
description: "Learn more about: MsSna_LuLua Class"
title: "MsSna_LuLua Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1eb3b759-5559-41a7-8dd7-3e322ce6981a
caps.latest.revision: 4
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# MsSna_LuLua Class
Describes a 3270 LU LUA resource.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_LuLua : MsSna_Lu3270  
{  
   boolean HighPriorityMode;  
};  
```  
  
## Properties  
 **HighPriorityMode**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to increase the priority for this LU; otherwise, **false**.  
  
## Remarks  
 **MsSna_LuLua** is often used for programmatic access.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
