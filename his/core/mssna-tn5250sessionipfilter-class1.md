---
description: "Learn more about: MsSna_TN5250SessionIPFilter Class"
title: "MsSna_TN5250SessionIPFilter Class1"
ms.custom: ""
ms.date: "12/12/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: reference
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
 Data Type: **String**Qualifiers: <strong>Key, MAXLEN(15)</strong>Access Type: Read-Only  
  
 The IP address or name of the computer assigned to the TN5250 session.  
  
 **AS400**  
 Data Type: **String**Qualifiers: <strong>Key, MAXLEN(8)</strong>Access Type: Read-Only  
  
 The IBM i definition.  
  
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
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
