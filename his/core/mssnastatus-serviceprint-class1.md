---
description: "Learn more about: MsSnaStatus_ServicePrint Class"
title: "MsSnaStatus_ServicePrint Class1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MsSnaStatus_ServicePrint Class
The **MsSnaStatus_ServicePrint** class represents an SNA Print service status.  
  
## Syntax  
  
```  
  
class MsSnaStatus_ServicePrint : MsSnaStatus_Config  
{  
   string Name;  
   sint32 Status;  
   string StatusText;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read-Only  
  
 The name of the Print Service. **Name** will be the same as the computer name.  
  
 **Status**  
 Data Type: **sint32** Access Type: Read-Only  
  
 The current status of the service. The following table describes the possible values for **Status**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Inactive|  
|1|Pending|  
|2|Stopping|  
|3|Active|  
  
 **StatusText**  
 Data Type: **String** Access Type: Read-Only  
  
 One of the **Status** values.  
  
 **Mode**  
 Data Type: **String** Access Type: Read-Only  
  
 The mode name for this session.  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|GetObject|Retrieves the instance.|  
|EnumerateInstances|Enumerates all instances of the object.|  
|ExecMethod|Executes the specified method.|  
|[Start](../core/mssnastatus-serviceprint-start-method1.md)|Starts the print service.|  
|[Stop](../core/mssnastatus-serviceprint-stop-method2.md)|Stops the print service|  
  
 For more information on **GetObject**, **EnumerateInstances**, and **ExecMethod**, see [IWbemServices interface](/windows/win32/wmisdk/iwbemservices-methods). 
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)