---
title: "Factors that Affect Maximum Sustainable Performance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "maximum sustainable throughput (MST), maintenance"
  - "monitoring, maximum sustainable thoughput (MST)"
  - "maintaining, maximum sustainable thoughput (MST)"
  - "maximum sustainable throughput (MST), monitoring"
  - "maximum sustainable throughput (MST), load patterns"
  - "maximum sustainable throughput (MST), sustainable load test"
  - "sustainable performance"
ms.assetid: 99b99655-bc77-425c-a133-204781d7c430
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Factors that Affect Maximum Sustainable Performance
Maximum sustainable throughput is directly impacted by a wide range of factors such as available server resources, the type of features used in the solution, message size, and overall message load. There are other factors to be considered though that may not be immediately obvious. The following factors should also be considered when estimating maximum sustainable performance:  
  
## Load Patterns  
 Messages do not typically flow into a production BizTalk Server environment at a predictable, consistent rate. More typically, business needs dictate that BizTalk Server process messages at a variable rate which exhibits peaks and valleys. When peaks occur, the BizTalk Server processing requirements may quickly jump from negligible to an overdrive condition where messages are received faster than they are processed. In this scenario, published messages are backlogged in the MessageBox database until BizTalk delivers the backlogged messages to the appropriate subscribers. As long as BizTalk Server is able to process the backlog of messages accumulated between peak load periods then this is not problematic.  
  
 Because of the typically variable pattern of message flow into a BizTalk Server environment, testing scenarios should be run for an extended period of time to ensure that the solution can sustain the desired throughput indefinitely, recovering from all peak loads over time.  
  
## Monitoring and Maintenance activities  
 During the life of a production solution, there is a host of monitoring and maintenance activities that can impact BizTalk performance and so should be factored into any testing scenarios. These activities include:  
  
-   **BizTalk Administration Console queries** These queries consume resources and affect overall throughput depending on the type and frequency of the query.  
  
-   **Backup, archiving, and purging activities** These activities also consume resources and should be factored into any testing scenarios. All BizTalk Server databases should be backed up periodically and their transaction logs truncated. If this is not performed the transaction log may grow un-checked and consume all of the available disk space for the transaction database. If tracking is being used, the tracking database must periodically be purged and optionally archived to keep it from growing too large. For more information about maintaining BizTalk Server databases, please see [Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md).  
  
## See Also  
 [Measuring Maximum Sustainable Tracking Throughput](../core/measuring-maximum-sustainable-tracking-throughput.md)