---
title: "MsHisTrace_SNANetMn Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55f23b43-11a2-497e-bb0b-a56a6f0fe9fe
caps.latest.revision: 4
---
# MsHisTrace_SNANetMn Class
The **MsHisTrace_SNANetMn** class contains SNA Net Management trace content.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsHisTrace_SNANetMn : MsHisTrace_Config  
{  
   string Name;  
   uint32 EnabledTraces;  
   Boolean InternalMessageTrace;  
   Boolean T3270Trace;  
   Boolean LU62Trace;  
   Boolean DLCTrace;  
   Boolean SnaTrace;  
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
  
 **DLCTrace**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable DLC tracing; otherwise, **false**.  
  
 **SnaTrace**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable SNA tracing; otherwise, **false**.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WmiSnaTrace WMI Provider Classes](../core/wmisnatrace-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../core/administration-and-management-programmer-s-guide1.md)