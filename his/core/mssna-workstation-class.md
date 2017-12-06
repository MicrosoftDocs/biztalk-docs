---
title: "MsSna_Workstation Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0c6dafd-70a7-47f0-ae8b-a4caac8a5fe0
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
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
 Data Type: **String**Qualifiers: **Key, MAXLEN(20)**Access Type: Read-Only  
  
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
 Data Type: **String**Qualifiers: **MAXLEN(20)**Access Type: Read/Write  
  
 The IP Subnet mask. Use **IPmask** only if **WorkstationIdType** is set to **IPSubnet**.  
  
 **DynRemote**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to enable users access to remote APPC LU as they are created; otherwise, **false**.  
  
 **Comment**  
 Data Type: **String**Qualifiers: **MAXLEN(25)**Access Type: Read/Write  
  
 An optional comment field.  
  
## Remarks  
 **MsSna_Workstation** can describe access to LUs and Pools.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes.md)   
 [Administration and Management Programmer's Guide](../Topic/Administration%20and%20Management%20Programmer's%20Guide1.md)