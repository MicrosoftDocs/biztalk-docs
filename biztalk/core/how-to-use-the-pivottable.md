---
title: "How to Use the PivotTable | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BAM views, pivot tables"
  - "BAM views, previewing data"
ms.assetid: af34494b-f577-4d36-9a9e-5d6e9c5fafbe
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Use the PivotTable
When you have defined a BAM view that includes dimensions and measures, you need to update one or more PivotTables associated with that view.  
  
 A PivotTable report in Excel is an interactive table that enables you to easily combine and compare large amounts of data. The values in its rows and columns can be rotated to look at different summaries of the displayed data. A PivotTable also enables you perform calculations on the data, such as aggregate counts or averages.  
  
 To use the PivotTable after you have created it, follow the steps in this procedure. For more information about using PivotTables, see the Microsoft Excel documentation.  
  
> [!NOTE]
>  When you create a real-time aggregation pivot table, it can contain a maximum of 14 dimension levels.  
  
> [!IMPORTANT]
>  If you define multiple PivotTables on the Excel Worksheet, it is possible the resulting tables can grow and overlap each other if the Activity returns a large dataset. In this scenario, you will receive "A PivotTable report cannot overlap another PivotTable report" when you refresh the data. You can correct this error by adding addition columns or rows between the pivot tables to allow the tables to grow with out overlapping.  
  
### To use the PivotTable  
  
1.  Create a BAM view to be used with a PivotTable. For more information about creating a BAM view, see [Defining a Business Activity View](../core/defining-a-bam-view.md)  
  
2.  Using the **PivotTable Field List**, drag-and-drop one or more available dimensions into the column and row areas of the PivotTable template.  
  
3.  Using the  **PivotTable Field List**, drag-and-drop one or more available measures into the data items area of the PivotTable template.  
  
     As you are updating the PivotTable, you will notice that it is populated with sample data. This helps you determine how the PivotTable should be configured.  
  
4.  Using the **PivotTable** toolbar, associate a chart with the PivotTable.  
  
5.  Save your Excel workbook.