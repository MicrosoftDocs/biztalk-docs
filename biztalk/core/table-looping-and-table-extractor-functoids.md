---
title: "Table Looping and Table Extractor Functoids | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2907aada-f11a-485c-85c8-03092803ccf7
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Table Looping and Table Extractor Functoids

## Overview
In a map, you commonly have one structure in the output instance message for each structure in the input instance message. However, there are cases when you need an input instance structure to produce multiple output instance structures. Table-driven looping enables you to create maps generating such multiple structures.  
  
 Table-driven looping uses the **Table Looping** functoid and the **Table Extractor** functoid. The **Table Looping** functoid has an internal table you configure. For each input record or field, the **Table Looping** functoid outputs the rows of the table, one at a time. For example, if there are ten records in the input instance message and two rows in the internal table of the **Table Looping**, the functoid outputs a total of twenty rows, two for each of the ten records. The **Table Extractor** functoid extracts the desired item from a row and passes it on to the output instance message.  
  
 For more details, see the **Table Looping Functoid Reference** and **Table Extractor Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## Next steps
  
-   [Table Looping Functoid](../core/table-looping-functoid.md)  
  
-   [Table Extractor Functoid](../core/table-extractor-functoid.md)  
  
-   [Table-Driven Looping Configuration](../core/table-driven-looping-configuration.md)  
  
-   [Table-Driven Looping Example](../core/table-driven-looping-example.md)