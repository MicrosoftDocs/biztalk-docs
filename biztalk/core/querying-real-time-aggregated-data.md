---
description: "Learn more about: Querying Real-Time Aggregated Data"
title: "Querying Real-Time Aggregated Data | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "queries [BAM], real-time data"
  - "BAM, real-time data"
ms.assetid: f60a34a1-ac64-47c7-8f83-1bc301170590
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Querying Real-Time Aggregated Data
The real-time aggregation (RTA) data is available for queries in a dynamically created SQL View in the BAM Primary Import database.  
  
 The name of this view is  
  
 **bam_\<** *ViewName* **\>_\<** *RTAName* **\>_RTAView**  
  
 Where  
  
 **\<** *ViewName* **\>** is the Name attribute of the View element in the BAM definition XML, which is the same as the View Name entered in the related Microsoft Excel wizards.  
  
 **\<** *RTAName* **\>** is the Name attribute of the RealTimeAggregation element in the BAM Definition XML, which BAM generates to be unique based on the view name.  
  
 It is important to note the following conditions when querying real-time aggregated data:  
  
-   The real-time aggregations must be configured to keep the aggregations for a given amount of time (the default is one day) and to never grow very large. The older aggregations should be available in the OLAP cubes instead.  
  
-   Any query against RTA must include filtering on a time dimension that will be inside the online window for the RTA data. This is necessary because BAM performs data maintenance for RTAs based  on the  timestamp on the BAM dataand is optimized to drop the data in chunks. Thus if you simply send the Transact-SQL command "`select *`", the results will fluctuate unpredictably.  
  
-   If the activity data is sent to BAM via the DirectEventStream, the real-time aggregated data has no latency – it appears instantaneously when the transaction in the calling Application commits.  
  
-   If the activity data is sent to BAM via the BufferedEventStream, the RTA data will show up for queries a few seconds later, depending on the load of the BAM Event Bus service(s) and the SQL server that hosts the BAM Primary Import database.  
  
-   BAM bases the real-time aggregation on a table that it maintains in synchronization with the changes or insertions in the activity data storage records using triggers. For more information, see [Activity Data Storage](../core/activity-data-storage.md). Thus, the real-time aggregation can have a significant performance impact. For more information, see [Real-Time Aggregations](../core/real-time-aggregations.md).  
  
## See Also  
 [Querying Scheduled Aggregated Data](../core/querying-scheduled-aggregated-data.md)   
 [Querying BAM Data](../core/querying-bam-data.md)
