---
description: "Learn more about: MsSnaStatus_ServiceSna Class"
title: "MsSnaStatus_ServiceSna Class1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MsSnaStatus_ServiceSna Class
The **MsSnaStatus_ServiceSna** class is used to get information on the status of the SNA service.  
  
## Syntax  
  
```  
  
class MsSnaStatus_ServiceSna : MsSnaStatus_Config  
{  
   string Name;  
   sint32 Status;  
   string StatusText;  
   Boolean bOutOfDate;  
   uint16 AppcSessions;  
   uint16 LU3270Sessions;  
   uint16 Users;  
}  
```  
  
## Properties  
 **Name**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read-Only  
  
 The name of the service. The string can contain more than one service, in the following format:\<ComputerName>, \<ComputerName>.01, \<ComputerName>.02, \<ComputerName>.03  
  
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
  
 **bOutOfDate**  
 Data Type: **Boolean** Access Type: Read-Only  
  
 **true** indicates that the configuration has changed and that the service must be restarted; otherwise, **false**.  
  
 **AppcSessions**  
 Data Type:**uint16** Access Type: Read-Only  
  
 Statistics on APPC sessions on the service.  
  
 **LU3270Sessions**  
 Data Type:**uint16** Access Type: Read-Only  
  
 Statistics on LU 3270 sessions on the service.  
  
 **Users**  
 Data Type:**uint16** Access Type: Read-Only  
  
 Statistics on users on the service.  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|**GetObject**|Retrieves the instance.|  
|**EnumerateInstances**|Enumerates all instances of the object.|  
|**ExecMethod**|Executes the specified method.|  
|[Start](../core/mssnastatus-servicesna-start-method1.md)|Starts the service.|  
|[Stop](../core/mssnastatus-servicesna-stop-method1.md)|Stops the service.|  
|[Pause](../core/mssnastatus-servicesna-pause-method1.md)|Pauses the service.|  
|[Resume](../core/mssnastatus-servicesna-resume-method2.md)|Resumes the service.|  
  
 For more information on **GetObject**, **EnumerateInstances**, and **ExecMethod**, see [IWbemServices interface](/windows/win32/wmisdk/iwbemservices-methods). 
  
## Remarks  
 There may be more than one service running on a computer.  
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11 and Windows 10  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)