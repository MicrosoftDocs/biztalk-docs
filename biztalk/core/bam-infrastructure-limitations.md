---
description: "Learn more about: BAM Infrastructure Limitations"
title: "BAM Infrastructure Limitations"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# BAM Infrastructure Limitations
The BAM infrastructure has the following design limitations for this release of BizTalk Server:  
  
-   Real-time aggregations (RTAs) do not support the MIN or MAX function.  
  
-   You cannot reference a one-level alias by more than one data dimension in one RTA view.  
  
-   Neither regular cube nor RTA supports distinct count measures. The BAM Management utility creates a default count measure for both regular cube and RTA. The default count is the total count of facts (also known as "activity instances"), and not the distinct count.  
  
-   Do not define multiple RTAs that use the same BAM activity. If you do so, the RTA data will be incorrect when you archive the BAM data.  
  
## BAM maximum number of objects  
 The following table lists the maximum number of objects in the BAM infrastructure.  
  
|Object|Implementation Limit|Reason|  
|------------|--------------------------|------------|  
|Checkpoints in Activity|1,000|SQL Server supports 1,024 Stored Procedure arguments and BizTalk Server uses three of the system procedures.|  
|Indexes in Activity|245|SQL Server supports 245 non-clustered indexes per table. BizTalk Server always creates an index on ActivityID.|  
|DataLength|4,000 Unicode characters|SQL variables of type NVARCHAR are used.|  
|ActivityRef|128|You can obtain the view by joining the Primary Import database and Relationship tables (two per Activity). SQL Server supports 256 tables in SELECT statement.|  
|Columns in View<br /><br /> (Aliases, durations, plus dimension levels)|150|SQL Server limit of 1,024 columns on the Staging Table of which BAM reserves 24 for system columns.|  
|Dimensions in OLAP cube|128|OLAP limitation - 128 dimensions per cube|  
|Measures in OLAP|1,024|OLAP limitation - 1,024 measures per cube. The Count measure is always created.|  
|Dimension levels in OLAP|64|OLAP limitation with an additional limit of 256 levels per cube.|  
|Dimension levels in RTA view|14 dimension levels|BAM creates an index on all dimension levels, a SQL Server index can be created on up to 16 columns, and BAM reserves two for system columns.|  
|Measures, hidden measures (default count, hidden SUM measures for AVG), and dimension levels in RTA view|1,024|Maximum of 1,024 columns in SQL table/view.|  
|ActivityViews|63|When you configure an alert, you are limited to 63 ActivityViews under SQL Server.|  
  
## BAM object names  
 The following table lists the limitations of object names in the BAM definition schema and Microsoft Excel spreadsheet.  
  
|Object Names|XSD Limitation|Excel Limitation|  
|------------------|--------------------|----------------------|  
|Checkpoint name|50 characters|50 characters|  
|Index name|100 characters|100 characters|  
|Duration name|100 characters|100 characters|  
|Alias name|50 characters|50 characters|  
|Activity name|48 characters|20 characters|  
|View name|18 characters|18 characters|  
|ActivityView name|52 characters (The name consists of the prefix "View" plus the 48 character view name.)|N/A (derived from Activity name)|  
|Cube name|20 characters|N/A (derived from View name)|  
|RealTimeAggregation name|48 characters|N/A (derived from Cube name)|  
|Dimension name|20 characters|20 characters|  
|Level name|20 characters|20 characters|  
|Measure name|20 characters|20 characters|  
|Alert name|128 characters|N/A|  
|Alert message|1024 characters|N/A|  
|Event Rule name|255 characters|N/A|  
|Event Provider name|255 characters|N/A|  
  
## See Also  
 [BAM Configuration Schema](../core/bam-configuration-schema.md)   
 [BAM Dynamic Infrastructure](../core/bam-dynamic-infrastructure.md)
