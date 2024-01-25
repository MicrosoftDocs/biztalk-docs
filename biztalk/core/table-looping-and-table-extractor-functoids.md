---
description: "Learn more about: Table Looping and Table Extractor Functoids"
title: "Table Looping and Table Extractor Functoids"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
