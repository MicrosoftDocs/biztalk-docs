---
title: "What Are Measures and Dimensions? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e6b12a4c-9be5-4cac-b5b9-ece376d28cb1
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Are Measures and Dimensions?
Dimensions and measures are the physical aspects of data aggregation. This topic describes what measures and dimensions are, using a BAM scenario to provide context.  
  
## Measures  
 Suppose that you define a BAM activity for an order management process in extremely simple terms consisting of three items:  
  
1. Process start time (an event in the real world)  
  
2. Process end time (also a real-world event)  
  
3. Process duration (a calculation of #2 - #1)  
  
   Aggregating data in this case is simply a matter of applying an aggregation function (for example, average, minimum, maximum, etc.) to a series of individual duration values (that is, the processing duration for each order).  
  
   The concept of "average duration" is a measure, and it is a single value. By itself, this measure yields information relevant to process management in that it indicates whether or not the process overall is behaving (in terms of timliness/throughput) as expected. However, in the absence of any other data (because "average duration" is a single value), understanding the meaning of the measure's actual value is harder For example, why did we have a spike in average duration this week? Was it due to a particular partner, program, product?  
  
## Dimensions  
 Dimensions are the context that help the consumer of measures understand the meaning of those measures.  
  
 Continuing the above example, suppose you add three additional items to the BAM activity for the order management process:  
  
1. trading partner name (who sent the order)  
  
2. account manager name (who is the sales contact)  
  
3. sales region  
  
   Since the activity now includes three possible data pivots (partner, account manager, region), aggregating this data now literally results in the creation of a three-dimensional cube at run-time.  
  
   It still begins with the first item of work, resulting in the creation of a single "average duration" measure. When the next item of work (initiated by the arrival of another purchase order) completes, if trading partner, account manager, and region are all the same as they were for the first item of work, then all that happens is that the "average duration" measure is recalculated, based now on two items (for example, the average of the two durations), to achieve a single "average duration" measure value.  
  
   As soon as an item comes where any of trading partner, account manager, or region are different than the set encountered so far, a new "average duration" measure value is created and maintained separate from the first one.  
  
   For example, if the trading partner on the third item of work was different than the previous two, the result is creation of a second "average duration" measure value along the trading partner dimension. Now you can review "average duration" values along the trading partner dimension and see things like "it takes us almost twice as long on average to process the orders from TradingPartnerX as it does for TradingPartnerY." And dimensions can be collapsed for viewing so that one can still see the overall "average duration" for the process independent of any trading partner or other dimension.  
  
   Finally, if trading partner, account manager, and region each have three and only three distinct values, once all permutations have occurred, the result is a Rubik's® Cube of data, where users can view each of 27 independently maintained "average duration" values, and the dimensions are each of three edges on the cube.  
  
   For additional information about dimensions and measures, see "About OLAP source data in PivotTable and PivotChart reports" in Excel Help.