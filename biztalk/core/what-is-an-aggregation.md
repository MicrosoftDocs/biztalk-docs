---
title: "What Is an Aggregation? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "OLAP cubes, BAM"
  - "BAM, aggregations"
  - "BAM, OLAP cubes"
  - "aggregations [BAM], OLAP cubes"
  - "aggregations [BAM], about aggregations"
  - "aggregations [BAM]"
ms.assetid: 77d40602-ef56-4a5b-a18f-56ccbff573a4
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Is an Aggregation?
Excel defines aggregations as pre-calculated summaries of data that improve query response time by having the answers ready before the questions are asked. For example, when a data warehouse fact table contains hundreds of thousands of rows, a query requesting the shipping schedules for two particular products can take a long time to answer if the fact table has to be scanned to compute the answer. However, the response can be almost immediate if the summarization data to answer this query has been pre-calculated.  
  
 The following figure displays an example of pre-calculated aggregation data.  
  
 ![](../core/media/bam-olap-cube.gif "bam_olap_cube")  
BAM OLAP Cube  
  
 The above figure summarizes the numbers of each product, shipped to specific locations over a two-month time period. Excel typically defines this data as measure. The data used for filtering and categorization, Excel defines as dimension.  
  
 For the user experience of browsing multidimensional data, see the PivotTable topic in Excel Help.  
  
 You can create multidimensional activity aggregations based on the data available in a specific view. Those aggregations contain measures (data to aggregate, such as dollar amount) and dimensions (used for filtering or grouping, such as State and City).  
  
 You can create the aggregations in the form of online analytical processing (OLAP) cubes, which represent a snapshot of the business at a specific time, or as real-time aggregations, which the business scenario determines and you see using the multidimensional structure in real time.  
  
## In This Section  
  
-   [Scheduled Aggregations](../core/scheduled-aggregations.md)  
  
-   [Real-Time Aggregations](../core/real-time-aggregations.md)