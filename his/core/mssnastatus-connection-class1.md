---
description: "Learn more about: MsSnaStatus_Connection Class"
title: "MsSnaStatus_Connection Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e4e52ebc-2a6f-40ca-aca6-723c98c13bc1
caps.latest.revision: 4
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# MsSnaStatus_Connection Class
The **MsSnaStatus_Connection** class represents a SNA service connection status.  
  
 The following is simplified MOF syntax.  
  
## Syntax  
  
```  
  
class MsSnaStatus_Connection : MsSnaStatus_Config  
{  
   string Name;  
   string ServiceName;  
   uint32 Status;  
   string StatusText;  
   uint32 InactiveState;  
   uint16 Failcode;  
   DateTime FailTime;  
}  
```  
  
## Properties  
 **Name**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read-Only  
  
 The name of the connection.  
  
 **ServiceName**  
 Data Type: **String** Access Type: Read-Only  
  
 Name of the SNA service to which this connection belongs.  
  
 **Status**  
 Data Type: **uint32** Access Type: Read-Only  
  
 Name of the SNA service to which this connection belongs.  
  
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
|1|Stopping|  
|2|Active|  
|3|Incoming|  
|4|OnDemand|  
|5|OnDemandIncoming|  
  
 **InactiveState**  
 Data Type: **uint32** Access Type: Read-Only  
  
 Additional detail on inactive connections. The following table describes the possible values for **InactiveState**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Inactive|  
|1|Incoming|  
|2|OnDemand|  
|3|OnDemandIncoming|  
  
 **Failcode**  
 Data Type: **uint16** Access Type: Read-Only  
  
 The failure code. 0 indicates a non-failure.  
  
 **FailTime**  
 Data Type: **DateTime** Access Type: Read-Only  
  
 The time the failure occurred. Valid only if **Failcode** is not 0.  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|**GetObject**|Retrieves the instance.|  
|**EnumerateInstances**|Enumerates all instances of the object.|  
|**ExecMethod**|Executes the specified method.|  
|[Start](../core/mssnastatus-connection-start-method1.md)|Starts the connection.|  
|[Stop](../core/mssnastatus-connection-stop-method2.md)|Stops the connection.|  
  
 For more information on **GetObject**, **EnumerateInstances**, and **ExecMethod**, see [IWbemServices interface](/windows/win32/wmisdk/iwbemservices-methods).  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)