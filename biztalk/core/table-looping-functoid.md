---
description: "Learn more about: Table Looping Functoid"
title: "Table Looping Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Table Looping functoids"
  - "Table Looping functoids, about Table Looping functoids"
ms.assetid: 6189a789-afe7-4e72-a778-2b0374db8f69
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Table Looping Functoid
The **Table Looping** functoid enables you to create a table of output values to use in creating the output instance message. The data in the table can consist of links and constants. The first input parameter to the **Table Looping** functoid configures the scope, or how many times the records will loop. The second input parameter for the **Table Looping** functoid determines how many columns are in the table, and the remaining inputs define possible cell values for the table, in no particular order. For more information about working with these properties, see [Table-Driven Looping Configuration](../core/table-driven-looping-configuration.md). Also see [Table-Driven Looping Example](../core/table-driven-looping-example.md).  
  
> [!NOTE]
>  The **Table Looping** functoid repeats with the looping record it is connected to. Within each iteration, it loops once per row in the table looping grid, producing multiple output loops.  
  
## See Also  
 [Table Extractor Functoid](../core/table-extractor-functoid.md)   
 [How to Add Table Looping and Table Extractor Functoids to a Map](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md)   
 [Advanced Functoids](../core/advanced-functoids.md)   
 [Index Functoid](../core/index-functoid.md)   
 [Iteration Functoid](../core/iteration-functoid.md)   
 [Looping Functoid](../core/looping-functoid.md)   
 [Record Count Functoid](../core/record-count-functoid.md)
