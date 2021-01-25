---
description: "Learn more about: MsHisTrace_COMTI Class"
title: "MsHisTrace_COMTI Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f9340303-8f6a-4fff-9f34-dca17dca6778
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# MsHisTrace_COMTI Class
The **MsHisTrace_COMTI** class describes tracing properties for Transaction Integrator (TI).  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsHisTrace_COMTI : MsHisTrace_Config  
{  
   string Name;  
   uint32 EnabledTraces;  
   Boolean InternalMessageTrace;  
   Boolean DPLHeaderTrace;  
   Boolean LU62Trace;  
   Boolean BriefLU62Trace;  
   Boolean COMTIProxy;  
   Boolean PipeLine;  
   Boolean BlackBoard;  
   Boolean GeneralService;  
   Boolean Repository;  
   Boolean DataTransit;  
   Boolean DataLayout;  
   Boolean Conversions;  
   Boolean Transport;  
   Boolean Registrar;  
   Boolean Scripting;  
   Boolean SessionManager;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read/Write  
  
 Name of the configuration file.  
  
 **EnabledTraces**  
 Data Type: **uint32** Qualifiers: **Qualifiers** Access Type: Read-Only  
  
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
  
 **DPLHeaderTrace**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable tracing of DPL Headers; otherwise, **false**.  
  
 **LU62Trace**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable LU 6.2 tracing; otherwise, **false**.  
  
 **BriefLU62Trace**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable a briefer version LU 6.2 tracing; otherwise, **false**.  
  
 **COMTIProxy**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable tracing of the COMPI Proxy API; otherwise, **false**.  
  
 **PipeLine**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable tracing of the PipeLine API; otherwise, **false**.  
  
 **BlackBoard**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable tracing of the BlackBoard API; otherwise, **false**.  
  
 **GeneralService**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable tracing of the GeneralService API; otherwise, **false**.  
  
 **Repository**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable tracing of the Repository API; otherwise, **false**.  
  
 **DataTransit**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable tracing of the DataTransit API; otherwise, **false**.  
  
 **Conversions**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable tracing of the Conversions API; otherwise, **false**.  
  
 **Transport**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable tracing of the Transport API; otherwise, **false**.  
  
 **Registrar**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable tracing of the Registrar API; otherwise, **false**.  
  
 **Scripting**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable tracing of the Scripting API; otherwise, **false**.  
  
 **SessionManager**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable tracing of the SessionManager API; otherwise, **false**.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WmiSnaTrace WMI Provider Classes](../core/wmisnatrace-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
