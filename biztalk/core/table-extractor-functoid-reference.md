---
title: "Table Extractor Functoid Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Table Extractor functoids, properties"
  - "Table Extractor functoids, about Table Extractor functoids"
ms.assetid: edb1c912-bdaf-4989-b61f-7bd8806f9566
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Table Extractor Functoid Reference
Use the **Table Extractor** functoid ( ![](../core/media/advtableextractor.gif "advtableextractor")) to output the data associated with a specified column for each row of the table looping grid of the specified **Table Looping** functoid.  
  
## Input  
 **Parameter 1:** An output link from a **Table Looping** functoid.  
  
 **Parameter 2:** The column number of the table looping grid from which this functoid is meant to retrieve data.  
  
## Output  
 **Output 1:** A set of values retrieved through the specified column of the table looping grid associated with the specified **Table Looping** functoid, where the number of values in the set is the number of rows in the table looping grid.  
  
## Remarks  
 You must use this functoid in conjunction with the **Table Looping** functoid.  
  
 This functoid may output multiple values, one per row in the table looping grid associated with the **Table Looping** functoid specified by the first input parameter.  
  
## See Also  
 [Advanced Functoids Reference](../core/advanced-functoids-reference.md)   
 [Advanced Functoids](../core/advanced-functoids.md)   
 [Table Looping and Table Extractor Functoids](../core/table-looping-and-table-extractor-functoids.md)   
 [How to Add Table Looping and Table Extractor Functoids to a Map](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md)