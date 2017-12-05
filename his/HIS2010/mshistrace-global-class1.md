---
title: "MsHisTrace_Global Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eae684e0-69d3-4b47-8c80-45887a14da59
caps.latest.revision: 4
---
# MsHisTrace_Global Class
The **MsHisTrace_Global** class contains the global settings for Microsoft® Host Integration Server tracing.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsHisTrace_Global : MsHisTrace_Config  
{  
   string Name;  
   uint32 AsyncThreadPriority;  
   Boolean AsyncTraceFlag;  
   uint32 FlipLength;  
   string TraceFileDirectory;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read/Write  
  
 Name of the configuration file.  
  
 **AsyncThreadPriority**  
 Data Type: **uint32** Access Type: Read/Write  
  
 If *AsyncTraceFlag* is **true**, *AsyncThreadFlag* specifies the level of priority for tracing to run within the Windows® operating system.  
  
 **AsyncTraceFlag**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to cause tracing to be run on a background thread; otherwise, **false**.  
  
 **FlipLength**  
 Data Type: **uint32** Access Type: Read/Write  
  
 The size a trace file should be before the trace utility switches to recording trace data in a second file.  
  
 **TraceFileDirectory**  
 Data Type: **String** Access Type: Read/Write  
  
 The directory in which to store trace files.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WmiSnaTrace WMI Provider Classes](../HIS2010/wmisnatrace-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../HIS2010/administration-and-management-programmer-s-guide1.md)