---
title: "MsSna_TN5250SessionIPFilter Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9fee3ade-4ed0-4d2e-830d-deca140dbdaf
caps.latest.revision: 4
---
# MsSna_TN5250SessionIPFilter Class
Contains the IP address or name assigned to a TN5250 session.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_TN5250SessionIPFilter : MsSna_Config  
{  
   String Name;  
   String AS400;  
   sint16 Type;  
   String SubnetMask;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String**Qualifiers: **Key, MAXLEN(15)**Access Type: Read-Only  
  
 The IP address or name of the computer assigned to the TN5250 session.  
  
 **AS400**  
 Data Type: **String**Qualifiers: **Key, MAXLEN(8)**Access Type: Read-Only  
  
 The AS/400 definition.  
  
 **Type**  
 Data Type: **sint16**Qualifiers: **Key**A value that indicates whether **Name** contains an IP address or a name. The following table describes the possible values for **Type**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Name|  
|1|IPAddress|  
  
 **SubnetMask**  
 Data Type: **String**Access Type: Read/Write  
  
 The IP Subnet mask, if an IP address is specified for 'Name'.  
  
## Remarks  
 You may assign multiple IP addresses or names in a single session.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../core/administration-and-management-programmer-s-guide1.md)