---
title: "MsSnaStatus_ClientConnections Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5a9f8fc-2194-4dc9-a17f-d44c86f2abc4
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
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
  
 For more information on **GetObject** and **EnumerateInstances**, see "IWbemServices interface" in the MSDN Library at http://msdn.microsoft.com/library.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes.md)   
 [Administration and Management Programmer's Guide](../Topic/Administration%20and%20Management%20Programmer's%20Guide1.md)