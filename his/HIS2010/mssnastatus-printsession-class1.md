---
title: "MsSnaStatus_PrintSession Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 946956e5-9699-4e29-b4d7-4c5a2392ea04
caps.latest.revision: 4
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
|[Start](../HIS2010/mssnastatus-printsession-start-method1.md)|Starts the print session.|  
|[Stop](../HIS2010/mssnastatus-printsession-stop-method1.md)|Stops the print session.|  
|[Pause](../HIS2010/mssnastatus-printsession-pause-method1.md)|Pauses the print session.|  
|[Restart](../HIS2010/mssnastatus-printsession-restart-method2.md)|Restarts the print session.|  
|[PA1Key](../HIS2010/mssnastatus-printsession-pa1key-method2.md)|Simulates pressing the PA1Key.|  
|[PA2Key](../HIS2010/mssnastatus-printsession-pa2key-method1.md)|Simulates pressing the PA2Key.|  
|[Cancel](../HIS2010/mssnastatus-printsession-cancel-method2.md)|Cancels the print session.|  
  
 For more information on **GetObject**, **EnumerateInstances**, and **ExecMethod**, see "IWbemServices interface" in the MSDN Library at http://msdn.microsoft.com/library.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../HIS2010/wmisnastatus-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](../HIS2010/administration-and-management-programmer-s-guide1.md)