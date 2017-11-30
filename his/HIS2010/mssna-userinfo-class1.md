---
title: "MsSna_UserInfo Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cee4ace2-5055-4e38-9e5e-59009f7f4451
caps.latest.revision: 6
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
 Data Type: **String**Qualifiers: **Key, MAXLEN(255)**Access Type: Read-Only  
  
 The user name.  
  
 **Comment**  
 Data Type: **String**Qualifiers: **MAXLEN(25)**Access Type: Read/Write  
  
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
 Data Type: **String**Qualifiers: **MAXLEN(8)**Access Type: Read/Write  
  
 A default local APPC LU to be used when the user starts APPC programs.  
  
 **DefRemoteLu**  
 Data Type: **String**Qualifiers: **MAXLEN(8)**Access Type: Read/Write  
  
 A default remote APPC LU to be used when the user starts APPC programs.  
  
 **Encryption**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to enable encryption between the client system and [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)]; otherwise, **false**.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../HIS2010/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../HIS2010/administration-and-management-programmer-s-guide1.md)