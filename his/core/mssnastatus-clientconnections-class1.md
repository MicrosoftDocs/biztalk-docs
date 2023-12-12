---
description: "Learn more about: MsSnaStatus_ClientConnections Class"
title: "MsSnaStatus_ClientConnections Class1"
ms.custom: ""
ms.date: "12/12/2023"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MsSnaStatus_ClientConnections Class
The **MsSnaStatus_ClientConnections** class represents a SNA service client connection status.  
  
## Syntax  
  
```  
  
class MsSnaStatus_ClientConnections : MsSnaStatus_Config  
{  
   string UserId;  
   string Domain;  
   string User;  
   string ClientMachine;  
   DateTime ClientConnectTime;  
   string ClientAppl;  
};  
```  
  
## Properties  
 **UserId**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read-Only  
  
 An arbitrary unique key.  
  
 **Domain**  
 Data Type: **String** Access Type: Read-Only  
  
 The domain on which the user is located.  
  
 **User**  
 Data Type: **String** Access Type: Read-Only  
  
 The username of the user.  
  
 **ClientMachine**  
 Data Type: **String** Access Type: Read-Only  
  
 The computer name on which the client application is running.  
  
 **ClientConnectTime**  
 Data Type: **DateTime** Access Type: Read-Only  
  
 The client-server connection start time.  
  
 **ClientAppl**  
 Data Type: **string** Access Type: Read-Only  
  
 The name of the client application.  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|GetObject|Retrieves the instance.|  
|EnumerateInstances|Enumerates all instances of the object.|  
  
 For more information on **GetObject** and **EnumerateInstances**, see [IWbemServices interface](/windows/win32/wmisdk/iwbemservices-methods).
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
