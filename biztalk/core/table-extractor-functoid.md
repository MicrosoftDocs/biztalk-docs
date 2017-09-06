---
title: "Table Extractor Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Table Extractor functoids"
  - "Table Extractor functoids, about Table Extractor functoids"
ms.assetid: cb5f6f15-f4e1-46d3-846e-6e2664699b62
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Table Extractor Functoid
The **Table Extractor** functoid determines which data to extract from each row of the looping grid as the **Table Looping** functoid presents the rows. You need one **Table Extractor** functoid for each output field. For example, suppose your input instance message had an address in a single format, but your output instance message needed the address in two formats with each format tagged. Then you would need a **Table Extractor** functoid for the tag and for each element of the address. For more information about configuring the **Table Extractor** functoid, see [Table-Driven Looping Configuration](../core/table-driven-looping-configuration.md). Also see [Table-Driven Looping Example](../core/table-driven-looping-example.md).  
  
## See Also  
 [Table Looping Functoid](../core/table-looping-functoid.md)   
 [How to Add Table Looping and Table Extractor Functoids to a Map](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md)   
 [Advanced Functoids](../core/advanced-functoids.md)   
 [Index Functoid](../core/index-functoid.md)   
 [Iteration Functoid](../core/iteration-functoid.md)   
 [Looping Functoid](../core/looping-functoid.md)   
 [Record Count Functoid](../core/record-count-functoid.md)