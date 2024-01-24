---
description: "Learn more about: How to Define Measures"
title: "How to Define Measures"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Define Measures
A measure defines how an activity is calculated. When you create a BAM view you can define a measure for the activity in the view. For example, for a purchase order activity, you can calculate the total PO amount, the number of POs, the average PO amount, and so on.  
  
 BAM supported measures include:  
  
-   Sum  
  
-   Count  
  
-   Average  
  
-   Minimum  
  
-   Maximum  
  
> [!NOTE]
>  The BAM Real-time Aggregation (RTA) feature doesn't currently support Minimum and Maximum measures. You can use those measures, but when you mark the Excel pivot table as an RTA, Minimum and Maximum are ignored.  
  
### To add new measures  
  
1. In the BAM View wizard, click **Next** until you see the **New BAM View: Aggregation Dimensions and Measures** page. Click **New Measures**.  
  
2. Type a name for your measure.  
  
3. From the drop-down list, select the **Base data item**.  
  
4. Click the **Aggregation type** you want to use. The choices include:  
  
   -   Sum  
  
   -   Count  
  
   -   Average  
  
   -   Minimum (not supported for RTAs).  
  
   -   Maximum (not supported for RTAs)  
  
5. Click **OK**. When you finish adding dimensions and measures, click **Next**.  
  
6. On the **New BAM View: Summary** page, review the information regarding your new view, and then click **Next**.  
  
7. Click **Finish** to complete the **BAM View Wizard**.  
  
   If you added measures and dimensions to your BAM view, you can add those items to the PivotTable in the Excel workbook. For more information about creating a PivotTable, see [How to Use the PivotTable](../core/how-to-use-the-pivottable.md).  
  
## See Also  
 [Defining Dimensions](../core/defining-dimensions.md)
