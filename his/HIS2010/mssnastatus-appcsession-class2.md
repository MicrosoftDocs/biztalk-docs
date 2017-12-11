---
title: "MsSnaStatus_AppcSession Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a91baf0-80c8-428f-8ad2-775d0c4599c0
caps.latest.revision: 4
---
# MsSnaStatus_AppcSession Class
The **MsSnaStatus_AppcSession** class represents an APPC session status.  
  
## Syntax  
  
```  
  
class MsSnaStatus_AppcSession : MsSnaStatus_Config  
{  
   string APPCLU;  
   string SessionID;  
   string PartnerLU;  
   string Mode;  
};  
```  
  
## Properties  
 **APPCLU**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read-Only  
  
 The Local APPC LU.  
  
 **SessionID**  
 Data Type: **String** Access Type: Read-Only  
  
 A unique ID for this session.  
  
 **PartnerLU**  
 Data Type: **String** Access Type: Read-Only  
  
 The Partner LU alias. **PartnerLU** can be a Remote LU or another Local LU.  
  
 **Mode**  
 Data Type: **String** Access Type: Read-Only  
  
 The mode name for this session.  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|GetObject|Retrieves the instance.|  
|EnumerateInstances|Enumerates all instances of the object.|  
|ExecMethod|Executes the specified method.|  
|[Stop](../HIS2010/mssnastatus-appcsession-stop-method2.md)|Stops the session.|  
  
 For more information on **GetObject**, **EnumerateInstances**, and **ExecMethod**, see "IWbemServices interface" in the MSDN Library at http://msdn.microsoft.com/library.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../HIS2010/wmisnastatus-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](../HIS2010/administration-and-management-programmer-s-guide1.md)