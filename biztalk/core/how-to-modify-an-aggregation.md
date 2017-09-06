---
title: "How to Modify an Aggregation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "aggregations [BAM], modifying"
  - "BAM portal, aggregations"
ms.assetid: dd5ce211-32d3-4e1d-8ee0-1225ec2c45fb
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Modify an Aggregation
You use PivotTable reports in Office Web Components the same way you use PivotTable reports in Excel. You can add and remove rows, columns, and filters to generate views of the aggregated data on which you can create alerts.  
  
## Prerequisites  
 To perform this procedure, you must have a deployed view that contains an aggregation.  
  
### To modify an aggregation  
  
1.  On the **Aggregations** page, from the **PivotTable Field List** window, drag the fields with data that you want to display in rows and drop them onto the left column of the grid to add row fields. If you don't see the field list, click within the outlines of the PivotTable drop areas, and make sure Show Field List appears. To see what levels of detail are available in fields that have levels, click the plus sign (+) next to the appropriate field.  
  
2.  Drag fields with data that you want to display across columns to the drop area labeled **Drop Column Fields Here**. Only fields that are designated as counts or progress fields can be dragged to this area.  
  
3.  If you add more than one data field, arrange these fields in the order you want: right-click a data field, point to **Order** on the shortcut menu, and use the commands on the **Order** menu to move the field.  
  
4.  To rearrange fields, drag them from one area to another. To remove a field, drag it out of the PivotTable report onto the navigation frame.  
  
5.  From the totals column in the PivotTable report, right-click the cell containing the total on which you are going to set an alert. Select **Create Alert** to open the Alert Management page.  
  
## See Also  
 [Aggregations on the BAM Portal Page](../core/aggregations-on-the-bam-portal-page.md)   
 [How to Set an Alert](../core/how-to-set-an-alert.md)