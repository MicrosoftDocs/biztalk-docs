---
description: "Learn more about: MsSna_UserInfo Class"
title: "MsSna_UserInfo Class2"
ms.custom: ""
ms.date: "12/12/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: reference
---
# MsSna_UserInfo Class
Base class for a User or Group account configured in SNA.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_UserInfo : MsSna_Config  
{  
   String Name;  
   sint32 UserType;  
   boolean DynRemote;  
   String DefLocalLu;  
   String DefRemoteLu;  
   boolean Encryption;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String**Qualifiers: <strong>Key, MAXLEN(255)</strong>Access Type: Read-Only  
  
 The user name.  
  
 **Comment**  
 Data Type: **String**Qualifiers: <strong>MAXLEN(25)</strong>Access Type: Read/Write  
  
 An optional comment field.  
  
 **UserType**  
 Data Type: **String**Access Type: Read-Only  
  
 The account type. The following table describes the possible values for **UserType**.  
  
|Value|Description|  
|-----------|-----------------|  
|1|User|  
|2|Group|  
|3|Domain|  
|4|Alias|  
|5|WellKnownGroup|  
|6|DeletedAccount|  
|7|Invalid|  
|8|Unknown|  
|9|Computer|  
  
 **DynRemote**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to let this user or group use dynamically created APPC LUs.  
  
 **DefLocalLu**  
 Data Type: **String**Qualifiers: <strong>MAXLEN(8)</strong>Access Type: Read/Write  
  
 A default local APPC LU to be used when the user starts APPC programs.  
  
 **DefRemoteLu**  
 Data Type: **String**Qualifiers: <strong>MAXLEN(8)</strong>Access Type: Read/Write  
  
 A default remote APPC LU to be used when the user starts APPC programs.  
  
 **Encryption**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to enable encryption between the client system and Host Integration Server; otherwise, **false**.  
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
