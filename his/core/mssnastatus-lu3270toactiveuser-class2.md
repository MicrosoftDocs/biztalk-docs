---
description: "Learn more about: MsSnaStatus_Lu3270ToActiveUser Class"
title: "MsSnaStatus_Lu3270ToActiveUser Class2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MsSnaStatus_Lu3270ToActiveUser Class
The **MsSnaStatus_Lu3270ToActiveUser** class represents an association between a User connection and a 3270 type LU.  
  
## Syntax  
  
```  
  
class MsSnaStatus_Lu3270ToActiveUser : MsSnaStatus_Association  
{  
   MsSnaStatus_Lu3270 ref PathToLU3270;  
   MsSnaStatus_ActiveUser ref PathToUser;  
};  
```  
  
## Properties  
 **PathToLU3270**  
 Data Type: **MsSnaStatus_Lu3270 ref** Qualifiers: **Key** Access Type: Read-Only  
  
 The path to the APPC session.  
  
 **PathToUser**  
 Data Type: **MsSnaStatus_ActiveUser ref** Qualifiers: **Key** Access Type: Read-Only  
  
 The path to the user.  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|GetObject|Retrieves the instance.|  
|EnumerateInstances|Enumerates all instances of the object.|  
  
 For more information on **GetObject** and **EnumerateInstances** see [IWbemServices interface](/windows/win32/wmisdk/iwbemservices-methods). 
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11 and Windows 10  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)