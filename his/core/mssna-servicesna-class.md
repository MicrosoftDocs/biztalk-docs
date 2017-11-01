---
title: "MsSna_ServiceSNA Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6fdcc403-329a-485c-a787-5848ecb4aa8e
caps.latest.revision: 4
---
# MsSna_ServiceSNA Class
Implements the SNA protocol, which contains the connections and LU resources.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_ServiceSNA : MsSna_Service  
{  
   String Name;  
   String Comment;  
   String ControlPoint;  
   String NetworkName;  
   String StatusText;  
   sint32 Status;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String**  
**Qualifier: Key, MAXLEN(20)** Access Type: Read-Only  
  
 The service name.  
  
 **Comment**  
 Data Type: **String**Qualifiers: **MAXLEN(25)** Access Type: Read/Write  
  
 An optional comment field.  
  
 **ControlPoint**  
 Data Type: **String**Qualifiers: **MAXLEN(8)** Access Type: Read/Write  
  
 The control point for this SNA node.  
  
 **NetworkName**  
 Data Type: **String**Qualifiers: **MAXLEN(8)** Access Type: Read/Write  
  
 The Network Name name for this SNA node.  
  
 **StatusText**  
 Data Type: **String**Access Type: Read-Only  
  
 The status of the service. The following table describes the possible values for **StatusText**.  
  
|Value|Description|  
|-----------|-----------------|  
|Not configured|The service is not currently configured.|  
|Inactive|The service is inactive.|  
|Stopping|The service is in the process of stopping.|  
|Active|The service is active.|  
|Out of Date|The service is out-of-date.|  
|Paused|The service is paused.|  
  
 **Status**  
 Data Type: **sint32**Access Type: Read-Only  
  
 The status of the service. The following table describes the status of the service:  
  
|Value|Description|  
|-----------|-----------------|  
|0|Not configured|  
|1|Inactive|  
|2|Inactive|  
|3|Stopping|  
|4|Active|  
|5||  
|6|Out-of-date|  
|7|Paused|  
|8||  
|9||  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|**Start**|Starts the service.|  
|**Stop**|Stops the service.|  
|**Pauses**|Pauses the service.|  
|**Resume**|Restarts a paused service.|  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes.md)