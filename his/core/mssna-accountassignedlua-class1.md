---
title: "MsSna_AccountAssignedLua Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d4404b30-6a20-495d-aa71-0b104721327f
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MsSna_AccountAssignedLua Class
Used to query for LUA LUs assigned to a specific workstation or user.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_AccountAssignedLua : MsSna_Assigned  
{  
   String Wks;  
   String IPAddress;  
   String MacAddress;  
   String Account;  
   String Service;  
   String LU;  
   boolean IsPool;  
   boolean ModelOverridable;  
};  
```  
  
## Properties  
 **Wks**  
 Data Type: **String** Qualifiers: **MAXLEN(20)** Access Type: Read/Write  
  
 The workstation name. By default, LUs assigned to all workstations are returned.  
  
 **IPAddress**  
 Data Type: **String** Qualifiers: **MAXLEN(20)** Access Type: Read/Write  
  
 The workstation IP. By default, LUs assigned to all workstations are returned.  
  
 **MacAddress**  
 Data Type: **String** Access Type: Read/Write  
  
 The user for which to query for LUs. By default, returns LUs assigned to all users.  
  
 **Account**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read/Write  
  
 The name of the service.  
  
 **Service**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read/Write  
  
 The SNA service on which to query for LUs.  
  
 **LU**  
 Data Type: **String** Qualifiers: **Key, MAXLEN(8)** Access Type: Read/Write  
  
 The name of the LU.  
  
 **IsPool**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to indicate that the returned LU is part of an LU pool; otherwise, **false**.  
  
 **ModelOverridable**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** if the LU has a display model which can be overridden.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)