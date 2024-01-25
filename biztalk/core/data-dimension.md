---
description: "Learn more about: Data Dimension"
title: "Data Dimension"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Data Dimension
Defining a data dimension allows the value of some text items in the BAM activity to be used on rows or columns. For example a data dimension named Product can be used to create the following table:  
  
|Product|Count|  
|-------------|-----------|  
|Tennis racquets|100|  
|Soccer balls|200|  
  
 Also, more than one data dimension can be defined in the BAM view wizard. For example, defining a data dimension named **Location** with levels for **State** and **City** can be used to create the following table:  
  
|&nbsp;|&nbsp;|&nbsp;|&nbsp;|  
|-|-|-|-|  
||California||Washington|  
||Los Angeles|San Francisco|Seattle|  
|Tennis racquets|50|20|30|  
|Soccer balls|130|50|20|  
  
 In this table, the Product dimension was used as the rows, and the Location dimension was used as the columns.  
  
## See Also  
 [Time Dimension](../core/time-dimension.md)   
 [Progress Dimension](../core/progress-dimension.md)   
 [Numeric Range Dimension](../core/numeric-range-dimension.md)   
 [Defining Dimensions](../core/defining-dimensions.md)
