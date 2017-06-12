---
title: "Configure Table Looping Functoid Dialog Box, Table Looping Grid Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.mapper.tablelooping"
helpviewer_keywords: 
  - "BizTalk Mapper, table looping grid"
  - "Table Extractor functoid"
ms.assetid: 8739d80f-87c1-4854-9a95-4a383f200eba
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure Table Looping Functoid Dialog Box, Table Looping Grid Tab
Use the **Configure Table Looping Grid** tab to configure a table of data and data sources in the source schema from which one or more **Table Extractor** functoids can be used to retrieve data at run-time and copy it to the output instance message as identified by a record or field in the destination schema.  
  
|Use this|To do this|  
|--------------|----------------|  
|Table cell drop-down lists|For this cell, select one of the relevant input parameters to this **Table Looping** functoid as the data to be associated with this cell.<br /><br /> The items in the drop-down list for each cell are the set of input parameters defined for this **Table Looping** functoid, not including the first two input parameters, which define the dimensions of this table. The input parameters can be constant data, output from another functoid, or a location in an instance message defined by the source schema. **Important:**  Providing descriptive labels for the input links to this **Table Looping** functoid are particularly useful in this scenario because the drop-down lists will show these friendly names rather than the associated XPath value.|  
|**Gated**|Configure whether the data in the first column is evaluated at run-time to determine whether processing the entire corresponding row will be skipped for the current iteration of the relevant record.<br /><br /> If the first cell is output from a **Logical** functoid, the row is evaluated if the value is **True**. If the first cell is a field, then the presence of data is treated as **True** and the row is evaluated. The absence of data is **False** and the row is skipped.|  
  
## See Also  
 [Table Looping Functoid Reference](../core/table-looping-functoid-reference.md)   
 [Table Extractor Functoid Reference](../core/table-extractor-functoid-reference.md)   
 [Table Looping and Table Extractor Functoids](../core/table-looping-and-table-extractor-functoids.md)   
 [Table-Driven Looping Example](../core/table-driven-looping-example.md)