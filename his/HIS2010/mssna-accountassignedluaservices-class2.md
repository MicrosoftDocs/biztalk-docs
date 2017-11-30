---
title: "MsSna_AccountAssignedLuaServices Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 02cc5aa9-5c5c-4137-af4b-d0a54736bd61
caps.latest.revision: 4
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
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../HIS2010/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../HIS2010/administration-and-management-programmer-s-guide1.md)