---
title: "Querying Scheduled Aggregated Data | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BAM, scheduled data"
  - "queries [BAM], scheduled data"
ms.assetid: fb785ec0-7862-4d83-bb6f-0ebd69a28ce6
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Querying Scheduled Aggregated Data
Scheduled aggregation data is available to queries through dynamically created OLAP cubes in the  BAM Analysis database.  
  
 The name of this cube is the same as the Name attribute of the View element in the BAM definition XML, which is the same as the view name entered in the Excel wizards. BAM refreshes this cube when you run the Data Transformation Services (DTS) package BAM_AN_\<*ViewName*>, where the \<*ViewName*> is the name of the view described you used in the Excel wizards.  
  
 It is important to note the following conditions when querying scheduled aggregated data:  
  
-   This is a virtual cube containing a snapshot of the business at the exact moment that the DTS package execution started. It contains aggregations both for the completed activities and for the ones still in progress. You can use the progress dimension to filter or group the aggregations accordingly.  
  
-   If you are never interested in the current activities (for example, if they complete very fast) you can query the corresponding real cube \<*ViewName*>#Completed.  
  
-   If you also have real-time aggregations, schedule the DTS package for refreshing the cube more frequently than the online window you set for the real-time aggregations. Otherwise, there will be a window of time for which you do not have aggregations.  
  
## See Also  
 [Querying BAM Data](../core/querying-bam-data.md)