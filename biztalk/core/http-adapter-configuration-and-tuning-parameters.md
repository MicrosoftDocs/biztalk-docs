---
description: "Learn more about: HTTP Adapter Configuration and Tuning Parameters"
title: "HTTP Adapter Configuration and Tuning Parameters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HTTP adapters, parameters"
  - "configuring [HTTP adapters], parameters"
  - "HTTP adapters, tuning"
  - "RequestQueueSize key [HTTP adapters]"
  - "HttpReceiveThreadsPerCpu key [HTTP adapters]"
  - "HttpOutTimeoutInterval key [HTTP adapters]"
  - "HttpOutInflightSize key [HTTP adapters]"
  - "configuring [HTTP adapters], tuning"
  - "DisableChunkEncoding key [HTTP adapters]"
  - "HttpOutCompleteSize key [HTTP adapters]"
ms.assetid: c8989a88-722a-40b5-94cf-4b6840add02e
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HTTP Adapter Configuration and Tuning Parameters
Several configuration and tuning parameters are accessible for the HTTP adapter through registry key entries and through the modification of the BTSNTSvc.exe.config file that is located in the root BizTalk Server installation directory.  
  
 **Registry Settings That Affect HTTP Adapter Performance**  
  
 The following table describes the registry settings that affect the performance of the HTTP adapter. Note that by default there are no HTTP adapter keys in the registry, so the HTTP adapter uses the default settings. If it is necessary to change the default settings, you need to create the following registry keys under the following locations in the registry:  
  
-   **DisableChunkEncoding**, **RequestQueueSize**, and **HttpReceiveThreadsPerCpu** must be defined in **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc.3.0\HttpReceive**.  
  
-   **HttpOutTimeoutInterval**, **HttpOutInflightSize**, and **HttpOutCompleteSize** must be defined in **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc{GUID}** where **GUID** is the ID of the host for the HTTP send handler.  
  
|Key name|Type|Default|Explanation|  
|--------------|----------|-------------|-----------------|  
|**DisableChunkEncoding**|DWORD|0|Regulates whether or not the HTTP receive adapter uses chunked encoding when sending responses back to the client.<br /><br /> Set to a nonzero value to turn off chunked encoding for HTTP receive adapter responses.<br /><br /> **Minimum value:** 0<br /><br /> **Maximum value:** Any nonzero value|  
|**RequestQueueSize**|DWORD|256|Defines the number of concurrent requests that the HTTP receive adapter processes at one time.<br /><br /> **Minimum value:**  10<br /><br /> **Maximum value:** 2048|  
|**HttpReceiveThreadsPerCpu**|DWORD|2|Defines the number of threads per CPU that are allocated to the HTTP receive adapter.<br /><br /> **Minimum value:** 1<br /><br /> **Maximum value:** 10|  
|**HttpOutTimeoutInterval**|DWORD|2000|Defines the interval in seconds that the HTTP send adapter will wait before timing out.<br /><br /> **Minimum value:** 500<br /><br /> **Maximum value:** 10000000|  
|**HttpOutInflightSize**|DWORD|100|This is the maximum number of concurrent HTTP requests that BizTalk Server HTTP send adapter instance will handle.<br /><br /> The recommended value for latency is between 3 to 5 times that of the **maxconnection** configuration file entry discussed below.<br /><br /> **Minimum value:** 1<br /><br /> **Maximum value:** 1024|  
|**HttpOutCompleteSize**|DWORD|5|Controls the size of the batch of messages that is returned from the HTTP send adapter. If the buffer is not full and there are outstanding responses then the adapter will wait for 1 second until it commits the batch.  For low-latency scenarios this should be set to 1 which will allow the adapter to send response messages immediately to the message box for processing.<br /><br /> **Minimum value:** 1<br /><br /> **Maximum value:** 1024|  
  
 **Configuration File Entry to Govern the Number of Concurrent Connections Made by the HTTP Send Adapter to a Particular Destination Server**  
  
 The number of concurrent connections that the HTTP adapter opens for a particular destination server can be configured by making an entry in the BTSNTSvc.exe.config file that is located in the root BizTalk Server installation directory.  
  
> [!NOTE]
>  This property will be applied to both HTTP and SOAP adapters if they send messages to the same destination HTTP server. The default value for the “maxconnnection” property is 2, the maximum value that can be set for the “maxconnection” property for all URIs is 20.  
  
 The following is an example of the configuration for the maximum connections property:  
  
```  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "https://www.contoso.com" maxconnection = "20" />  
      <add address = "http://www.northwind.com" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## See Also  
 [Configuring the HTTP Adapter](../core/configuring-the-http-adapter.md)
