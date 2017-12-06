---
title: "MsSna_TN3270SessionIPFilter Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 47f2b3ba-b9e4-4a0c-98c3-e81c5c638cd9
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# MsSna_TN3270SessionIPFilter Class
An IP address or name assigned to a TN3270 session.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_TN3270SessionIPFilter : MsSna_Config  
{  
   String Name;  
   String Session;  
   sint16 Type;  
   String SubnetMask;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String**Qualifiers: **Key, MAXLEN(15)**Access Type: Read-Only  
  
 The IP address or name of the computer assigned to the TN3270 session.  
  
 **Session**  
 Data Type: **String**Qualifiers: **Key, MAXLEN(8)**Access Type: Read-Only  
  
 The TN3270 session name.  
  
 **Type**  
 Data Type: **sint16**Qualifiers: **Key**Access Type: Read/Write  
  
 A value that determines if **Name** contains an IP address or a name. The following table describes the possible values for **Type**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Name|  
|1|IPAddress|  
  
 **SubnetMask**  
 Data Type: **String**Access Type: Read/Write  
  
 The IP Subnet mask, if an IP address is specified for **Name**.  
  
## Remarks  
 Multiple IP addresses or names can be assigned to one session.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes.md)   
 [Administration and Management Programmer's Guide](../Topic/Administration%20and%20Management%20Programmer's%20Guide1.md)