---
title: "MsSnaStatus_Lu3270 Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb8eaf56-ed13-407a-9e23-13b524240c0c
caps.latest.revision: 5
---
# MsSnaStatus_Lu3270 Class
The **MsSnaStatus_Lu3270** class represents a SNA Service display LU, printer LU, or LUA LU status.  
  
## Syntax  
  
```  
  
class MsSnaStatus_Lu3270 : MsSnaStatus_Config  
{  
   string Name;  
   string ConnectionName;  
   uint32 Status;  
   string StatusText;  
   uint32 ActiveState;  
   string HostAppl;  
}  
```  
  
## Properties  
 **Name**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read-Only  
  
 The name of the LU.  
  
 **ConnectionName**  
 Data Type: **String** Access Type: Read-Only  
  
 The connection on which this LU is defined.  
  
 **Status**  
 Data Type: **uint32** Access Type: Read-Only  
  
 The current status of the connection. The following table describes the potential values for **Status**.  
  
|Value|Description|  
|-----------|-----------------|  
|0||  
|1|Inactive|  
|2|Pending|  
|3|Stopping|  
|4|Active|  
  
 **StatusText**  
 Data Type: **String** Access Type: Read-Only  
  
 One of the status values. The following table describes the potential values for **StatusText**.  
  
|Value|Description|  
|-----------|-----------------|  
|0||  
|1|Inactive|  
|2|Pending|  
|3|Stopping|  
|4|Available|  
|5|InSession|  
|6|SSCP|  
  
 **ActiveState**  
 Data Type: **uint32** Access Type: Read-Only  
  
 Additional detail on active ULs. The following table describes the possible values for **ActiveState**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Available|  
|1|InSession|  
|2|SSCP|  
  
 **HostAppl**  
 Data Type: **string** Access Type: Read-Only  
  
 The short name of the host application.  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|**GetObject**|Retrieves the instance.|  
|**EnumerateInstances**|Enumerates all instances of the object.|  
|**ExecMethod**|Executes the specified method.|  
|[Stop](../HIS2010/mssnastatus-lu3270-stop-method2.md)|Stops the LU.|  
  
 For more information on **GetObject**, **EnumerateInstances**, and **ExecMethod**, see "IWbemServices interface" in the MSDN Library at http://msdn.microsoft.com/library.  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../HIS2010/wmisnastatus-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](../HIS2010/administration-and-management-programmer-s-guide1.md)