---
description: "Learn more about: Use performance counters with the WCF LOB Adapter SDK"
title: "Use performance counters with the WCF LOB Adapter SDK | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6b928eaf-2ab6-40a6-a1dd-804d4e89541e
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Use performance counters with the WCF LOB Adapter SDK
You can use the performance tool to automatically collect performance data from local or remote computers that are running the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. You can define start and stop times for automatic log generation, manage multiple logging sessions from a single console window, and set an alert on a computer that enables a message to be sent or a log to be started when your criteria are met. This topic discusses the performance counters for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].  
  
## Performance Objects and Counters  
 When you install the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], a single performance object named "ServiceModel Adapters" is installed. The performance object contains a number of different performance counters. A performance object measures the activity for a given resource, application, or service. Performance objects and counters obtain performance data from the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], features, and services on your computer as they are used. This performance data is typically named for the component that generates the data. Performance counters are used for gathering specific information or data for a given performance object.  
  
 When selecting counters from the ServiceModel Adapters performance object, you can choose to only monitor information specific adapter instances by selecting the instance from the Select Instances list. Each adapter instance will be listed in the format of \<ProcessId\>@\<ConnectionString\>. For example, 115@echo:&#124;&#124;host&#124;temp?echoprefix=pre indicates the echo adapter instance running in process 115.  
  
 For information about performance counters in WCF, see [WCF Performance Counters](/dotnet/framework/wcf/diagnostics/performance-counters/).
  
### ServiceModel Adapters Metadata Cache Performance Counters  
 The following table summarizes the cache performance counters that can be used to monitor the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].  
  
|Counter|Description|  
|-------------|-----------------|  
|% Cache read hits|Percentage of metadata read hits in the adapter cache.|  
|Metadata Resolved|Number of metadata items resolved by the adapter.|  
|% Cache full|Percentage of the cache size limit in use.|  
  
### ServiceModel Adapters Connection Performance Counters  
 The following table summarizes the connection performance counters that can be used to monitor the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].  
  
|Counter|Description|  
|-------------|-----------------|  
|Aborted Connections|Number of aborted target system connections.|  
|In-use Connections|Number of currently in-use target system connections.|  
|Opened Connections|Number of currently open target system connections.|  
|Ready Connections|Number of available target system connections.|  
|Pending Connection Requests|Number of pending target system connection requests.|  
  
### ServiceModel Adapters Message Exchange Performance Counters  
 The following table summarizes the message exchange performance counters that can be used to monitor the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].  
  
|Counter|Description|  
|-------------|-----------------|  
|Outbound Calls|Number of outbound calls from the adapter to the target system.|  
|Outbound Calls/sec|Number of outbound calls per second from the adapter to the target system.|  
  
## See Also  
 [Troubleshoot adapter created using the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/troubleshoot-adapter-created-using-the-wcf-lob-adapter-sdk.md)