---
description: "Learn more about: MsHisTrace_SNAMngAgent Class"
title: "MsHisTrace_SNAMngAgent Class1"
ms.custom: ""
ms.date: "12/12/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: reference
---
# MsHisTrace_SNAMngAgent Class
The **MsHisTrace_SNAMngAgent** class contains tracing properties for the SNA Manage Agent.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsHisTrace_SNAMngAgent : MsHisTrace_Config  
{  
   string Name;  
   uint32 EnabledTraces;  
   Boolean InternalMessageTrace;  
};  
```  
  
## Remarks  
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
 **Platforms**: WindowsWindows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WmiSnaTrace WMI Provider Classes](../core/wmisnatrace-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
