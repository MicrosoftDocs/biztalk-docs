---
title: "MsSna_ServiceTN5250 Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 92d5e098-05da-4d39-a8ab-6101db1f92b1
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MsSna_ServiceTN5250 Class
Enables clients to connect via the TN5250 protocol to a host.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_ServiceTN5250 : MsSna_Service  
{  
   String Name;  
   String Comment;  
   sint32 Port;  
   String StatusText;  
};  
```  
  
## Remarks  
 **Name**  
 Data Type: **String**Qualifiers: <strong>Key, MAXLEN(16)</strong>Access Type: Read-Only  
  
 The TN5250 service name. **Name** is the same as the computer name.  
  
 **Comment**  
 Data Type: **String**Qualifiers: <strong>MAXLEN(25)</strong>Access Type: Read/Write  
  
 An optional comment field.  
  
 **Port**  
 Data Type: **sint32**Qualifiers: <strong>MINVALUE(0), MAXVALUE(9999)</strong>Access Type: Read/Write  
  
 The default port number for the TN5250 service. Port can be overridden on a per-session basis. Use 0 for the default TN5250 port.  
  
 **StatusText**  
 Data Type: **String**Access Type: Read-Only  
  
 The current status of the service. The following table describes the possible values for **StatusText**.  
  
|Value|Description|  
|-----------|-----------------|  
|Not configured|The service is not configured.|  
|Inactive|The service is inactive.|  
|Pending|The service is pending.|  
|Stopping|The service is stopping.|  
|Active|The service is active.|  
|Out of Date|The service is out-of-date.|  
|Paused|The service is paused.|  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|[Start](../core/mssna-servicetn5250-start-method1.md)|Starts the service.|  
|[Stop](../core/mssna-servicetn5250-stop-method2.md)|Stops the service.|  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)