---
title: "Real-Time Aggregations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BAM, aggregations"
  - "aggregations [BAM], real-time data"
ms.assetid: 0ef44641-e067-4108-b318-f4373ca8fa8f
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Real-Time Aggregations
In some cases, specific slices of the multidimensional aggregations are so time-sensitive that you want them to be available in real time. For example, your business is selling perishable products and you want the aggregation of product quantity in different stages of delivery to be available in real time. At the same time, you want other aggregations such as the age of your typical customers, but only at the end of the month for business intelligence analysis.  
  
 BAM implements real-time aggregation (RTA) as a table maintained by triggers from the activity storage tables. In the case when your business deals with purchase orders (PO), the RTA view may look like the example in the following figure.  
  
 ![](../core/media/bam-realtime-aggregations.gif "bam_realtime_aggregations")  
BAM Real-time Aggregations  
  
 In this figure, if a new PO of $100 from Redmond is received, BAM adds a contribution to the cells in the corresponding row for {Redmond, InProcess} by performing an operation like `Count=Count+1` and `Amount=Amount+$100`.  
  
 Later, if the same order ships, then BAM removes this contribution from the row {Redmond, InProcess} and adds it to the row {Redmond, Shipped}.  
  
 BAM maintains the data inside RTA for a given online window, and then deletes it. You can configure the online window by changing the corresponding row of the table **bam_Metadata_RealTimeAggregations**.  
  
 The following statements also apply to real-time aggregations:  
  
- Real-time aggregations significantly affect the speed at which BAM can write data. Thus, you should only define the most important slices of the aggregation structure as RTA.  
  
- The limitation of the dimension levels for real-time aggregations is 14. For example, if you create a Data Dimension Location for State and City, this counts as two levels (State and City). For Progress Dimensions the number of levels is the depth of the tree, and for Time Dimensions it is the count of all sub-units. For example, a Time Dimension for Year, Month, Day, Hour will count as four levels.  
  
- BAM does not support real-time aggregations of type **Min** and **Max**. The aggregations that BAM supports are **Count**, **Sum**, and **Average**.  
  
- You must always create a time dimension for RTA and always use it in all data slices, because the data in RTA is aged based on the server time stamp, and not on any specific business milestone.  
  
- Do not define multiple RTAs that use the same BAM activity. If you do so, the RTA data will be incorrect when you archive the BAM data.  
  
  Real-time aggregations significantly affect the speed at which BAM can write data. Thus, you should only define the most important slices of the aggregation structure as RTA.  
  
  The limitation of the dimension levels for real-time aggregations is 14. For example, if you create a Data Dimension Location for State and City, this counts as two levels (State and City). For Progress Dimensions the number of levels is the depth of the tree, and for Time Dimensions it is the count of all sub-units. For example, a Time Dimension for Year, Month, Day, Hour will count as four levels.  
  
  BAM does not support real-time aggregations of type **Min** and **Max**. The aggregations that BAM supports are **Count**, **Sum**, and **Average**.  
  
  Do not define multiple RTAs that use the same BAM activity. If you do so, the RTA data will be incorrect when you archive the BAM data.  
  
## See Also  
 [What Is an Aggregation?](../core/what-is-an-aggregation.md)