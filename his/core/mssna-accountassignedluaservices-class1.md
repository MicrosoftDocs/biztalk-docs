---
title: "MsSna_AccountAssignedLuaServices Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 946797b3-2a9a-444f-b04b-dfacdbb8ed33
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MsSna_AccountAssignedLuaServices Class
Used to query for services on which a specific workstation or user has LUA LUs/pools.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_AccountAssignedLuaServices : MsSna_Assigned  
{  
   String Wks;  
   String IPAddress;  
   String MacAddress;  
   String Account;  
   String Service;  
};  
```  
  
## Properties  
 **Wks**  
 Data Type: **String** Qualifiers: **MAXLEN(20)** Access Type: Read/Write  
  
 The workstation name. By default, those assigned to all workstations are returned.  
  
 **IPAddress**  
 Data Type: **String** Qualifiers: **MAXLEN(20)** Access Type: Read/Write  
  
 The workstation IP address. By default, those assigned to all workstations are returned.  
  
 MacAddress  
 Data Type: **String** Qualifiers: **MAXLEN(20)** Access Type: Read/Write  
  
 Returns services with LUs configured to a specific media access control (MAC) address.  
  
 **Account**  
 Data Type: **String** Access Type: Read/Write  
  
 The user to which the LUs are assigned. By default, returns services with LUs assigned to all users.  
  
 **Service**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read/Write  
  
 Returns the name of the service.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](../core/administration-and-management-programmer-s-guide1.md)