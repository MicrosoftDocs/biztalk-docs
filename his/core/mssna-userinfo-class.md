---
title: "MsSna_UserInfo Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aff8d231-c24a-41db-bff4-327bfe9c021b
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
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
  
 **true** to enable encryption between the client system and [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)]; otherwise, **false**.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes.md)   
 [Administration and Management Programmer's Guide](../Topic/Administration%20and%20Management%20Programmer's%20Guide1.md)