---
title: "MsSna_ServicePrint Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f06e0b6b-0d13-4a80-96be-a976b641d339
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MsSna_ServicePrint Class
Contains print sessions.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_ServicePrint : MsSna_Service  
{  
   String Name;  
   boolean NoEventLogOnSkippingTransparentSection;  
   boolean UseProportionalFontChange;  
   boolean FlushFinalFF;  
   boolean DelayPrintStart;  
   boolean AlwaysDoNL;  
   boolean NoSpaceAfterFF;  
   boolean DoAllFF;  
   boolean IgnoreCharsUnder3F;  
   boolean UseFixedTabs;  
   sint32 ActivationRetryInterval;  
   sint32 ActivationRetryLimit;  
   String StatusText;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String**Qualifiers: <strong>Key, MAXLEN(16)</strong>Access Type: Read/Write  
  
 The Host Print service name. **Name** is the same as the machine name.  
  
 **NoEventLogOnSkippingTransparentSection**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to prevent an entry in the Event Log every time a print service skips a transparent section found while printing a host print job; otherwise, **false**.  
  
 **UseProportionalFontChange**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to prevent overlapping characters in documents containing nonfixed type fonts printed through Host Print service; otherwise, **false**.  
  
 **FlushFinalFF**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to cause Host Print service to explicitly form-feed the document at the end of a print job; otherwise, **false**.  
  
 **DelayPrintStart**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to delay the start of the print job until printable data is received by Host Print services; otherwise, **false**.  
  
 **AlwaysDoNL**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to insert a new line when the Host Print service determines that the Maximum Print Position has been reached for a particular line of data; otherwise, **false**.  
  
 **NoSpaceAfterFF**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to prevent print services from inserting a space character following a form feed; otherwise, **false**.  
  
 **DoAllFF**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to force the printer driver to honor all form-feed commands; otherwise, **false**.  
  
 **IgnoreCharsUnder3F**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to cause the Host Print service to ignore hexadecimal characters 3F and below; otherwise, **false**.  
  
 **UseFixedTabs**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to disable normal tab functionality (such as aligning tabs in columns) and interpret each tab as a fixed number of spaces; otherwise, **false**.  
  
 **ActivationRetryInterval**  
 Data Type: **sint32**Access Type: Read/Write  
  
 The number of seconds to wait before trying to print the job again. The default value is 10 seconds.  
  
 **ActivationRetryLimit**  
 Data Type: **sint32**Access Type: Read/Write  
  
 The number of times Host Print service attempts to activate the APPC conversation following a terminated connection. The default value is -1 (infinite).  
  
 **StatusText**  
 Data Type: **String**Access Type: Read/Write  
  
 The current status of Host Print service. The following table describes the possible values for **StatusText**.  
  
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
|[Start](../core/mssna-serviceprint-start-method1.md)|Starts the service.|  
|[Stop](../core/mssna-serviceprint-stop-method1.md)|Stops the service.|  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)