---
title: "BAM Interceptor Performance Counters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9b64ae1-4d94-4c3c-add1-fa020713be5c
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BAM Interceptor Performance Counters
Performance counters allow you to monitor specific aspects of work performed by the BAM interceptors. Performance counters can help you identify and troubleshoot server performance issues.  
  
 The following table lists the performance counters available for the BAM interceptors. The performance counters category is “BAM Interceptor.”  
  
|Counter|Description|  
|-------------|-----------------|  
|Avg. Failed BAM Events/Flush Avg|The average number of failed BAM events that occurred during a flush of data to the Primary Import database.|  
|Successful BAM Events/Flush|The average number of successful BAM events that occurred during a data flush to the Primary Import database. The events may not be persisted to the database if the transaction is rolled back.|  
|Avg. Extraction sec/BAM Event|The average amount of time spent extracting BAM events.|  
|Avg. Flush sec/BAM Event|The average amount of time spent flushing BAM events.|  
|Total Failed BAM Events During Flush|The total number of failed BAM events that occurred during the data flush|  
|Total Successful BAM Events During Flush|The total number of successful BAM events flushed to the Primary Import database. The events may not be persisted to the database if the transaction is rolled back.|  
  
## See Also  
 [BAM Performance Counters](../core/bam-performance-counters.md)