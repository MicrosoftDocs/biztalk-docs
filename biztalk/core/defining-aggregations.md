---
title: "Defining Aggregations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "aggregations [BAM], creating"
  - "Excel add-in [BAM], creating aggregations"
  - "aggregations [BAM], Excel add-in"
  - "aggregations [BAM], about aggregations"
ms.assetid: d5bf22d5-f491-4b08-a604-c7158e6e282f
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Defining Aggregations
Excel defines **aggregations** as pre-calculated summaries of data that improve query response time by having the answers ready before the questions are asked. For example, when a data warehouse fact table contains hundreds of thousands of rows, a query requesting the shipping schedules for two particular products can take a long time to answer if the fact table has to be scanned to compute the answer. However, the response can be almost immediate if the summarization data to answer this query has been pre-calculated.  
  
 The following figure displays an example of pre-calculated aggregation data.  
  
 ![](../core/media/bam-olap-cube.gif "bam_olap_cube")  
Pre-calculated Aggregation Data  
  
 The above figure summarizes the numbers of each product, shipped to specific locations over a two-month time period. Excel typically defines this data as **measure**. The data used for filtering and categorization, Excel defines as **dimension**.  
  
> [!NOTE]
>  BAM does not support using named instances for [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services.  
  
 For the user experience of browsing multidimensional data, see the Pivot table topic in Excel Help.  
  
## In This Section  
  
-   [How to Define Measures](../core/how-to-define-measures.md)  
  
-   [Defining Dimensions](../core/defining-dimensions.md)  
  
-   [How to Use the PivotTable](../core/how-to-use-the-pivottable.md)  
  
-   [Defining Real-Time Aggregations](../core/defining-real-time-aggregations.md)  
  
## See Also  
 [Defining a BAM View](../core/defining-a-bam-view.md)