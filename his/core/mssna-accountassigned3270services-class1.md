---
description: "Learn more about: MsSna_AccountAssigned3270Services Class"
title: "MsSna_AccountAssigned3270Services Class1"
ms.custom: ""
ms.date: "12/12/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: reference
---
# MsSna_AccountAssigned3270Services Class
Used to query for services on which a specific workstation or user has 3270 LUs/pools.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_AccountAssigned3270Services : MsSna_Assigned  
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
 Data Type: **String** Qualifiers: **MAXLEN(20)** Access Type: Read-Only  
  
 The workstation IP address. By default, those assigned to all workstations are returned.  
  
 **MacAddress**  
 Data Type: **String** Qualifiers: **MAXLEN(20)** Access Type: Read/Write  
  
 Returns services with LUs configured to a specific media access control (MAC) address.  
  
 **Account**  
 Data Type: **String** Access Type: Read/Write  
  
 The user to which the LUs are assigned. By default, returns services with LUs assigned to all users.  
  
 **Service**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read/Write  
  
 The name of the service.  
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
