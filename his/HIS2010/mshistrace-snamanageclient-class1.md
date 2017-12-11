---
title: "MsHisTrace_SNAManageClient Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7ccc35a3-d29b-48f3-94e1-c967048e9e94
caps.latest.revision: 4
---
# MsHisTrace_SNAManageClient Class
The **MsHisTrace_SNAManageClient** contains tracing properties for the SNA Manage Client.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsHisTrace_SNAManageClient : MsHisTrace_Config  
{  
   string Name;  
   uint32 EnabledTraces;  
   Boolean InternalMessageTrace;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read/Write  
  
 Name of the configuration file.  
  
 **EnabledTraces**  
 Data Type: **uint32** Access Type: Read/Write  
  
 Bitmap indicating which Internal Trace conditions to record. The following table describes the possible values for **EnabledTraces**.  
  
|Value|Description|  
|-----------|-----------------|  
|1|Fatal trace mask|  
|2|Error trace mask|  
|4|Debug trace mask|  
|8|State trace mask|  
|16|Function trace mask|  
|32|Message trace mask|  
|64|Custom trace mask|  
|128|Plan enter exit mask|  
  
 **InternalMessageTrace**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable tracing of internal messages; otherwise, **false**.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WmiSnaTrace WMI Provider Classes](../HIS2010/wmisnatrace-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../HIS2010/administration-and-management-programmer-s-guide1.md)