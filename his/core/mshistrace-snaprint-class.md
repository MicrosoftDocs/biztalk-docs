---
title: "MsHisTrace_SNAPrint Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7b878d8c-3ccf-44fa-87af-5ac1c5066b7a
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# MsHisTrace_SNAPrint Class
The **MsHisTrace_SNAPrint** class contains tracing properties for the Host Print service.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsHisTrace_SNAPrint : MsHisTrace_Config  
{  
   string Name;  
   uint32 EnabledTraces;  
   Boolean InternalMessageTrace;  
   Boolean T3270Trace;  
   Boolean LU62Trace;  
   Boolean APPCTrace;  
   Boolean CPICTrace;  
   Boolean LUATrace;  
   Boolean CSVTrace;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read/Write  
  
 Name of the configuration file.  
  
 **EnabledTraces**  
 Data Type: **uint32** Access Type: Read/Write  
  
 Bitmap that indicates which Internal Trace conditions to record. The following table describes the possible values for **EnabledTraces**.  
  
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
  
 **T3270Trace**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable T3270 tracing; otherwise, **false**.  
  
 **LU62Trace**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable LU 6.2 tracing; otherwise, **false**.  
  
 **APPCTrace**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable APPC tracing; otherwise, **false**.  
  
 **CPICTrace**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable CPI-C tracing; otherwise, **false**.  
  
 **LUATrace**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable LUA tracing; otherwise, **false**.  
  
 **CSVTrace**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable CSV tracing; otherwise, **false**.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WmiSnaTrace WMI Provider Classes](../core/wmisnatrace-wmi-provider-classes.md)   
 [Administration and Management Programmer's Guide](../Topic/Administration%20and%20Management%20Programmer's%20Guide1.md)