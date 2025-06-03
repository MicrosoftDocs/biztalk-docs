---
description: "Learn more about: MsSnaStatus_ServiceSharedFolder Class"
title: "MsSnaStatus_ServiceSharedFolder Class2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: reference
---
# MsSnaStatus_ServiceSharedFolder Class
The **MsSnaStatus_ServiceSharedFolder** class represents a TN3270 service status.  
  
## Syntax  
  
```  
  
class MsSnaStatus_ServiceSharedFolder : MsSnaStatus_Config  
{  
   string Name;  
   sint32 Status;  
   string StatusText;  
}  
```  
  
## Properties  
 **Name**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read-Only  
  
 The name of the service. **Name** will be the same as the local computer name.  
  
 **Status**  
 Data Type: **sint32** Qualifiers: **Key** Access Type: Read-Only  
  
 The status of the service. The following table describes the potential values for **Status**.  
  
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
|EnumerateInstances|Enumerates the instance.|  
|ExecMethod|Executes the specified method.|  
|[Start](../core/mssnastatus-servicesharedfolder-start-method2.md)|Starts the service.|  
|[Stop](../core/mssnastatus-servicesharedfolder-stop-method2.md)|Stops the service.|  
  
 For more information on **GetObject**, **EnumerateInstances**, and **ExecMethod**, see [IWbemServices interface](/windows/win32/wmisdk/iwbemservices-methods). 
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
