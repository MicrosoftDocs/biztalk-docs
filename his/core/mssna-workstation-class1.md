---
description: "Learn more about: MsSna_Workstation Class"
title: "MsSna_Workstation Class1"
ms.custom: ""
ms.date: "12/12/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: reference
---
# MsSna_Workstation Class
Describes a workstation configured in SNA, specified by name or IP address.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_Workstation : MsSna_Config  
{  
   String Name;  
   sint32 IdType;  
   sint16 Secure;  
   String IPmask;  
   boolean DynRemote;  
   String Comment;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String**Qualifiers: <strong>Key, MAXLEN(20)</strong>Access Type: Read-Only  
  
 The workstation ID. **Name** is usually the workstation name.  
  
 **IdType**  
 Data Type: **sint32**Access Type: Read/Write  
  
 The type of workstation specified in **Name**. The following table describes the possible values for **IdType**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Name|  
|1|IPAddress|  
|2|IPSubnet|  
  
 **Secure**  
 Data Type: **sint16**Access Type: Read/Write  
  
 Describes a value indicating whether the workstation can access LUs that are not directly assigned to it. The following table describes the possible values for **Secure**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|False|  
|1|True|  
  
 **IPmask**  
 Data Type: **String**Qualifiers: <strong>MAXLEN(20)</strong>Access Type: Read/Write  
  
 The IP Subnet mask. Use **IPmask** only if **WorkstationIdType** is set to **IPSubnet**.  
  
 **DynRemote**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to enable users access to remote APPC LU as they are created; otherwise, **false**.  
  
 **Comment**  
 Data Type: **String**Qualifiers: <strong>MAXLEN(25)</strong>Access Type: Read/Write  
  
 An optional comment field.  
  
## Remarks  
 **MsSna_Workstation** can describe access to LUs and Pools.  
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
