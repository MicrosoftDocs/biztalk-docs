---
description: "Learn more about: MsSnaStatus_ServiceTN3270 Class"
title: "MsSnaStatus_ServiceTN3270 Class2"
ms.custom: ""
ms.date: "12/12/2023"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MsSnaStatus_ServiceTN3270 Class
The **MsSnaStatus_ServiceTN3270** class represents a TN3270 service status.  
  
## Syntax  
  
```  
  
class MsSnaStatus_ServiceTN3270 : MsSnaStatus_Config  
{  
   string Name;  
   sint32 Status;  
   string StatusText;  
}  
```  
  
## Properties  
 **Name**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read-Only  
  
 The service name. **Name** will be identical to the local computer name.  
  
 **Status**  
 Data Type: **sint32** Access Type: Read-Only  
  
 The current status of the service. The following table describes the possible values for **Status**.  
  
|Value|Description|  
|-----------|-----------------|  
|0||  
|1|Inactive|  
|2|Pending|  
|3|Stopping|  
|4|Active|  
  
 **StatusText**  
 Data Type: **String** Access Type: Read-Only  
  
 One of the status values.  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|GetObject|Retrieves the instance.|  
|EnumerateInstances|Enumerates all instances of the object.|  
|ExecMethod|Executes the specified method.|  
|[Start](../core/mssnastatus-servicetn3270-start-method2.md)|Starts the service.|  
|[Stop](../core/mssnastatus-servicetn3270-stop-method1.md)|Stops the service.|  
  
 For more information on **GetObject**, **EnumerateInstances**, and **ExecMethod**, see [IWbemServices interface](/windows/win32/wmisdk/iwbemservices-methods). 
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
