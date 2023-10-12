---
description: "Learn more about: BAM Performance Counters"
title: "BAM Performance Counters"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# BAM Performance Counters
Performance counters allow you to monitor specific aspects of work performed by the BAM Event Bus Service. Performance counters can help you identify and troubleshoot server performance issues.  
  
 The following table lists the performance counters available in Business Activity Monitoring.  
  
|Counter|Description|  
|-------------|-----------------|  
|Events being processed|The number of events the BAM Event Bus Service is currently processing|  
|Batches being processed|The number of batches the BAM Event Bus Service is currently processing|  
|Events Committed|The number of events the BAM Event Bus Service has committed to SQL Server in the last second.|  
|Records Committed|The number of records the BAM Event Bus Service has committed to SQL Server in the last second.|  
|Batches Committed|The number of batches the BAM Event Bus Service has committed to SQL Server in the last second.|  
|Total Events|The number of events the BAM Event Bus Service has processed since you started it.|  
|Total Records|Then number of records the BAM Event Bus Service has processed since you started it.|  
|Total Batches|Then number of batches the BAM Event Bus Service has processed since you started it.|  
|Total Failed Batches|Then number of batches the BAM Event Bus Service has failed to process since you started it.|  
|Total Failed Events|Then number of events the BAM Event Bus Service has failed to process since you started it.|  
  
 The performance counters are located in the Performance Monitor (perfmon) under the BizTalk:TDDS performance object. The instance name of the performance counters are a combination of the source server name and the name of the source database. If two of the BAM Event Bus Services are running on the same computer against two different source databases, you will see two instances of the BAM Event Bus Service counters.  
  
## See Also  
 [Managing the BAM Event Bus Service](../core/managing-the-bam-event-bus-service.md)   
 [BAM Security Recommendations](../core/bam-security-recommendations.md)   
 [Managing BAM](../core/managing-bam.md)
