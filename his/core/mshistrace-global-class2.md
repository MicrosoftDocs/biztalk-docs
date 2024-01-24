---
description: "Learn more about: MsHisTrace_Global Class"
title: "MsHisTrace_Global Class2"
ms.custom: ""
ms.date: "12/12/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WmiSnaTrace WMI Provider Classes](../core/wmisnatrace-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
