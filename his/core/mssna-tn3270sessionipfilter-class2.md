---
description: "Learn more about: MsSna_TN3270SessionIPFilter Class"
title: "MsSna_TN3270SessionIPFilter Class2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
 Data Type: **String**Qualifiers: <strong>Key, MAXLEN(15)</strong>Access Type: Read-Only  
  
 The IP address or name of the computer assigned to the TN3270 session.  
  
 **Session**  
 Data Type: **String**Qualifiers: <strong>Key, MAXLEN(8)</strong>Access Type: Read-Only  
  
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
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11 and Windows 10  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
