---
title: "MsSna_LuLua Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e75ce139-e6a8-42b6-afff-a2d2b791e9bf
caps.latest.revision: 4
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
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../HIS2010/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../HIS2010/administration-and-management-programmer-s-guide1.md)