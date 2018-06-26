---
title: "MsSna_ServiceSharedFolder Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d40832d7-da91-465d-934f-abd002ad3bb0
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MsSna_ServiceSharedFolder Class
Describes a service for AS/400 file access.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_ServiceSharedFolder : MsSna_Service  
{  
   String Name;  
   String Comment;  
   String StatusText;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String**Qualifiers: <strong>Key, MAXLEN(16)</strong>Access Type: Read-Only  
  
 The Shared Folder Gateway service name. **Name** is the same as the computer name.  
  
 **Comment**  
 Data Type: **String**Qualifiers: <strong>MAXLEN(25)</strong>Access Type: Read/Write  
  
 An optional comment field.  
  
 **StatusText**  
 Data Type: **String**Access Type: Read/Write  
  
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
|[Start](../core/mssna-servicesharedfolder-start-method2.md)|Starts the service.|  
|[Stop](../core/mssna-servicesharedfolder-stop-method2.md)|Stops the service.|  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)