---
title: "Error - Table Looping Data Not Valid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.tableLoopingDataNotValid"
ms.assetid: 19c38e79-bab0-4899-ae24-e1485327e891
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Table Looping Data Not Valid
**Error Code**  
  
 btm1065  
  
 **Explanation**  
  
 The table of data associated with the relevant **Table Looping** functoid is not valid, probably due to an incorrectly configured second input parameter to the functoid, or an incorrectly configured table looping grid.  
  
 **User Action**  
  
 Ensure that the input parameters to the **Table Looping** functoid, as accessed through the **Input Parameters** property and the **Configure \<Functoid\> Functoid** dialog box, are as shown in the following table.  
  
|Table Looping functoid input parameter number|Description|  
|---------------------------------------------------|-----------------|  
|1|Link from a record or field in the source schema, the number of occurrences of which an input instance message controls the number of times the set of associated **Table Extractor** functoids are run.|  
|2|The number of columns in the data table configured through the **Table Looping Grid** property of the relevant **Table Looping** functoid.|  
|3 – 100|Constants and links (from the source schema or output from other functoids) that will become possible sources of data with the table looping grid.|  
  
 Also, ensure that you properly configure the table looping grid, as accessed through the **Table Looping Grid** property and the **Table Looping Configuration** dialog box. A constant or link value must be chosen for every cell that will be accessed by an associated **Table Extractor** functoid.