---
description: "Learn more about: MsSnaStatus_Lu3270 Class"
title: "MsSnaStatus_Lu3270 Class2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
|[Stop](../core/mssnastatus-lu3270-stop-method1.md)|Stops the LU.|  
  
 For more information on **GetObject**, **EnumerateInstances**, and **ExecMethod**, see [IWbemServices interface](/windows/win32/wmisdk/iwbemservices-methods).  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)