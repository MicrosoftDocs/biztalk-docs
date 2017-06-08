---
title: "New Dimension Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts06.bam.workbook.newdimension"
ms.assetid: f8fc8a9d-b52a-400f-9ef8-1925340ca21f
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# New Dimension Dialog Box
Use the **New Dimension** dialog box to create a new category in an Analysis Services (OLAP) cube to describe the data contained in a table.  
  
 The contents of the New Dimension dialog box change based on the dimension type you choose. You can create the following types of dimensions:  
  
-   **Data Dimension**. A dimension that you use to categorize the aggregations based on the value of some text items in the BAM activity.  
  
-   **Numeric Range Dimension**. A dimension that enables you to categorize aggregations based on friendly names of given numeric ranges.  
  
-   **Progress Dimension**. A dimension to represent the creation of aggregations with respect to the progress of activities that are still in process.  
  
-   **Time Dimension**. A dimension that enables you to create aggregations for defined time segments.  
  
 The following table shows the details for the New Dimension dialog box when you create a data dimension.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Dimension name**|Type a descriptive name for the dimension you are creating.|  
|**Dimension type**|From the drop-down list, select Data Dimension.|  
|**Available data items**|Select the item or items that you want to include in the dimension.|  
|**Dimension levels**|Select the item or items that you want to remove from the dimension or change the order of in the dimension.|  
|**Add**|Click to add the items selected in the Available data items list.|  
|**Add All**|Click to add all of the items in the Available data items list.|  
|**Remove**|Click to remove the selected item from the Dimension levels list.|  
|**Remove All**|Click to remove all of the data items from the Dimension levels list.|  
|**Move Up**|Click to move the selected data item up in the Dimension levels list.|  
|**Move Down**|Click to move the selected data item down in the Dimension levelslist.|  
  
 The following table shows the details for the New Dimension dialog box when you create a numeric range dimension.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Dimension name**|Type a descriptive name for the dimension you are creating.|  
|**Dimension type**|From the drop-down list, select Numeric Range Dimension. **Note:**  You must create at least two ranges.|  
|**Base data item**|From the drop-down list, select the base data item for the numeric range dimension.|  
|**Available ranges**|Select a range you want to edit or delete.|  
|**New Range**|Click to create a new range for the dimension. The New Range dialog box opens.|  
|**Edit**|Click to edit the selected range.|  
|**Delete**|Click to delete the selected range.|  
  
 The following table shows the details for the New Dimension dialog box when you create a progress dimension.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Dimension name**|Type a descriptive name for the dimension you are creating.|  
|**Dimension type**|From the drop-down list, select Progress Dimension.|  
|**Progress milestones and stages**|Select a stage for which you want to create a child or sibling, or which you want to edit or delete.|  
|**New Stage**|Click to create a new transient child stage. If you want to create the child stage in relation to an existing stage, in the Progress stages list, select the existing stage, and then click New Child. Opens the New Progress Stage dialog box. **Important:**  Child stages must be created before sibling stages.|  
|**New Milestone**|Click to create a new non-transient sibling stage. If you want to create the sibling stage in relation to an existing stage, in the Progress stages list, select the existing stage, and then click New Sibling. Opens the New Progress Stage dialog box.|  
|**Edit**|Click to edit the selected progress stage.|  
|**Delete**|Delete the selected progress stage.|  
  
 The following table shows the details for the New Dimension dialog box when you create a time dimension.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Dimension name**|Type a descriptive name for the dimension you are creating.|  
|**Dimension type**|From the drop-down list, select Time Dimension.|  
|**Base business milestone**|From the drop-down list, select the base business milestone for the time dimension.|  
|**Year, quarter, month**|Click to display aggregate data by year, quarter, and month.|  
|**Year, quarter, month, day**|Click to display aggregate data by year, quarter, month, and day.|  
|**Year, quarter, month, day, hour, minute**|Click to display aggregate data by year, quarter, month, day, hour, and minutes.|  
|**Year, month**|Click to display aggregate data by year and month.|  
|**Year, month, day**|Click to display aggregate data by year, month, and day.|  
|**Year, month, day, hour minute**|Click to display aggregate data by year, month, day, hour, and minutes.|  
|**Year, week**|Click to display aggregate data by year and week.|  
|**Year, week, day**|Click to aggregate data by year, week, and day.|  
|**Year, week, day, hour, minute**|Click to display aggregate data by year, week, day, hour, and minutes.|  
  
## See Also  
 [Defining Dimensions](../core/defining-dimensions.md)