---
title: "How to Integrate BAM with SQL Server Reporting Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e2d66b7-c8eb-4871-8a47-544955ccd51e
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Integrate BAM with SQL Server Reporting Services
Creating a report based on data in the BAM infrastructure use the typical tasks associated with creating a report for any other SQL Server data source. For more information about creating a report with Report Designer, see [http://go.microsoft.com/fwlink/?LinkId=82437](http://go.microsoft.com/fwlink/?LinkId=82437).  
  
## Prerequisites  
 You must have permissions to access the data necessary to create the report.  
  
### How to Create a Report in BAM by Using SQL Server Reporting Service  
  
1.  Select the data source from which to create the report.  
  
     BAM provides two data sources to which Reporting Services can point.  
  
    |Data Source|Description|  
    |-----------------|-----------------|  
    |BAM Primary Import database|Contains views on activity instances and real-time aggregations. Select Type=”Microsoft SQL Server” and Connection String=”Data Source=\<*server name*>; Initial Catalog=\<*database name*>”, where \<*server name*> and \<*database name*> are the server and database names of your Bam Primary Import database.|  
    |BAM Analysis database|Contains data that is used to query the analysis cube. Select Type=”Microsoft SQL Server Analysis Server” and Connection String=”Data Source=\<*server name*>; Initial Catalog=\<*database name*>”, where \<*server name*> and \<*database name*> are the server and database names of your BAM Analysis database.|  
  
2.  Design the query. For the BAM Primary Import database, there are two types of views:  
  
    |View Name|Description|  
    |---------------|-----------------|  
    |dbo.bam_\<*view name*>_\<*activity name*>View_View.|This view contains instance data.|  
    |dbo.bam_\<*view name*>_\<*real time aggregation pivot table name*>_RTAView|This view contains data used in real-time aggregations.|  
  
    > [!NOTE]
    >  You can type **select \* from view** to return the desired result set. For the BAM Analysis database, click the query builder and drag the dimensions and measures of the cube named \<*view name*> to return the desired result set.  
  
## Next Steps  
 Complete the steps in the Report Wizard to specify which data you are going to present and how the data is to be presented.  
  
## See Also  
 [Managing BAM Databases](../core/managing-bam-databases.md)