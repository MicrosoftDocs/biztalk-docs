---
title: "Numeric Range Dimension | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "aggregations [BAM], Numeric Range dimension"
  - "Numeric Range dimension [BAM]"
ms.assetid: a874ce44-b034-498f-ba58-114028dbef2c
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Numeric Range Dimension
The numeric range dimension allows aggregations to be categorized based on friendly names of given ranges. For example, a business analyst can define a numeric range dimension named PO Size with the ranges Small for purchase orders between 0-$100, Medium for purchase orders between $100 to $1,000, and Large for purchase orders exceeding $1,000.  
  
> [!NOTE]
>  If a purchase order amount is not in the defined ranges, for example, a purchase order amount is less than 0, and then an "Out of range" row will be automatically created by BAM to accommodate the out-of-range data.  
  
> [!NOTE]
>  You cannot create two numeric range dimensions that reference the same data alias.  
  
## See Also  
 [How to Use the PivotTable](../core/how-to-use-the-pivottable.md)   
 [Progress Dimension](../core/progress-dimension.md)   
 [Data Dimension](../core/data-dimension.md)   
 [Time Dimension](../core/time-dimension.md)   
 [Defining Dimensions](../core/defining-dimensions.md)