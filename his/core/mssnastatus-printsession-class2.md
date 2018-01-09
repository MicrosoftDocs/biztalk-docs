---
title: "MsSnaStatus_PrintSession Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7115d8cc-32d9-40e7-ba79-f8836ce9c2b2
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MsSnaStatus_PrintSession Class
The **MsSnaStatus_PrintSession** class represents an SNA Print session status.  
  
## Syntax  
  
```  
  
class MsSnaStatus_PrintSession : MsSnaStatus_Config  
{  
   string Name;  
   uint32 Status;  
   string StatusText;  
   uint32 PrintState;  
   uint16 Type;  
}  
```  
  
## Properties  
 **Name**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read-Only  
  
 A unique ID for the session.  
  
 **Status**  
 Data Type: **sint32** Access Type: Read-Only  
  
 The current status of the service. The following table describes the possible values for **Status**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Inactive|  
|1|Pending|  
|2|Stopping|  
|3|Active|  
  
 **StatusText**  
 Data Type: **String** Access Type: Read-Only  
  
 One of the **Status** values. The following describes the possible values for **StatusText**.  
  
|Value|  
|-----------|  
|Inactive|  
|Pending|  
|Stopping|  
|Spooling|  
|Printing|  
|Paper Out|  
|Printer Offline|  
|Printer Error|  
|Printer Paused|  
|Printer Idle|  
|InSession|  
|Ready|  
|Paused|  
|Unknown|  
  
 **PrintState**  
 Data Type: **String** Access Type: Read-Only  
  
 The printer state that indicates the status of the printer or any printer errors. The following table describes the possible values for **PrintState**.  
  
|Value|  
|-----------|  
|Spooling|  
|Printing|  
|Paper Out|  
|Printer Offline|  
|Printer Error|  
|Printer Paused|  
|Printer Idle|  
|InSession|  
|Ready|  
|Paused|  
|Unknown|  
  
 **Type**  
 Data Type: **uint16** Access Type: Read-Only  
  
 The type of print session. The following table describes the possible values for **Type**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|3270|  
|1|APPC|  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|GetObject|Retrieves the instance.|  
|EnumerateInstances|Enumerates all instances of the object.|  
|ExecMethod|Executes the specified method.|  
|[Start](../core/mssnastatus-printsession-start-method2.md)|Starts the print session.|  
|[Stop](../core/mssnastatus-printsession-stop-method2.md)|Stops the print session.|  
|[Pause](../core/mssnastatus-printsession-pause-method2.md)|Pauses the print session.|  
|[Restart](../core/mssnastatus-printsession-restart-method1.md)|Restarts the print session.|  
|[PA1Key](../core/mssnastatus-printsession-pa1key-method1.md)|Simulates pressing the PA1Key.|  
|[PA2Key](../core/mssnastatus-printsession-pa2key-method2.md)|Simulates pressing the PA2Key.|  
|[Cancel](../core/mssnastatus-printsession-cancel-method1.md)|Cancels the print session.|  
  
 For more information on **GetObject**, **EnumerateInstances**, and **ExecMethod**, see "IWbemServices interface" in the MSDN Library at http://msdn.microsoft.com/library.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)