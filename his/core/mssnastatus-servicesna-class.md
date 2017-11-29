---
title: "MsSnaStatus_ServiceSna Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2a036caf-1000-4beb-9566-f85a851447da
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
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
|[Start](../core/mssnastatus-servicesna-start-method.md)|Starts the service.|  
|[Stop](../core/mssnastatus-servicesna-stop-method.md)|Stops the service.|  
|[Pause](../core/mssnastatus-servicesna-pause-method.md)|Pauses the service.|  
|[Resume](../core/mssnastatus-servicesna-resume-method.md)|Resumes the service.|  
  
 For more information on **GetObject**, **EnumerateInstances**, and **ExecMethod**, see "IWbemServices interface" in the MSDN Library at http://msdn.microsoft.com/library.  
  
## Remarks  
 There may be more than one service running on a computer.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes.md)   
 [Administration and Management Programmer's Guide](../Topic/Administration%20and%20Management%20Programmer's%20Guide1.md)