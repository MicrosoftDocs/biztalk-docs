---
description: "Learn more about: MsSnaStatus_APPCSessionToActiveUser Class"
title: "MsSnaStatus_APPCSessionToActiveUser Class1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MsSnaStatus_APPCSessionToActiveUser Class
The **MsSnaStatus_APPCSessionToActiveUser** class represents an association between a User connection and an APPC session.  
  
## Syntax  
  
```  
  
class MsSnaStatus_APPCSessionToActiveUser : MsSnaStatus_Association  
{  
   MsSnaStatus_AppcSession ref PathToAPPCSession;  
   MsSnaStatus_ActiveUser ref PathToUser;  
};  
```  
  
## Properties  
 **PathToAPPCSession**  
 Data Type: **MsSnaStatus_AppcSession ref** Qualifiers: **Key** Access Type: Read-Only  
  
 The path to the APPC session.  
  
 **PathToUser**  
 Data Type: **String**Qualifiers: **Key** Access Type: **MsSnaStatus_ActiveUser ref**  
  
 The path to the user.  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|GetObject|Retrieves the instance.|  
|EnumerateInstances|Enumerates all instances of the object.|  
  
 For more information on **GetObject** and **EnumerateInstances**, see [IWbemServices interface](/windows/win32/wmisdk/iwbemservices-methods). 
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11 and Windows 10  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)