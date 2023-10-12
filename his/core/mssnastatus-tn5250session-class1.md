---
description: "Learn more about: MsSnaStatus_TN5250Session Class"
title: "MsSnaStatus_TN5250Session Class1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MsSnaStatus_TN5250Session Class
The **MsSnaStatus_TN5250Session** class represents a TN5250 session status.  
  
## Syntax  
  
```  
  
class MsSnaStatus_TN5250Session : MsSnaStatus_Config  
{  
   string TNSessionID;  
   string APPCLU;  
   string PartnerLU;  
   string Mode;  
   string Client;  
};  
```  
  
## Properties  
 **TNSessionID**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read-Only  
  
 An arbitrary unique ID representing the session ID.  
  
 **APPCLU**  
 Data Type: **String** Access Type: Read-Only  
  
 APPC Local LU alias.  
  
 **PartnerLU**  
 Data Type: **String** Access Type: Read-Only  
  
 APPC Partner LU alias. **PartnerLU** can be a Remote LU or another Local LU.  
  
 **Mode**  
 Data Type: **String** Access Type: Read-Only  
  
 The mode name for this session.  
  
 **Client**  
 Data Type: **String** Access Type: Read-Only  
  
 The client computer name or IP address.  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|GetObject|Retrieves the instance.|  
|EnumerateInstances|Enumerates all instances of the object.|  
  
 For more information on **GetObject** and **EnumerateInstances**, see [IWbemServices interface](/windows/win32/wmisdk/iwbemservices-methods). 
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)