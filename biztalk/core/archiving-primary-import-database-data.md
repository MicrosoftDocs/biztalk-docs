---
title: "Archiving Primary Import Database Data | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Primary Import database [BAM], archiving data"
  - "archived data, BAM"
  - "managing [BAM], archiving data"
  - "data, archiving [BAM]"
ms.assetid: 4a014a59-0578-41fa-9441-8b582f54bbe8
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Archiving Primary Import Database Data
An administrator can specify the time window for archiving activity instance data in the primary import database. You use the OnlineWindowTimeUnit and OnlineWindowTimeLength properties in the BAM_Metadata_Activities table in the BAMPrimaryImport database.  
  
 If business users have deployed multiple activities, you can specify a different time window for each activity. For information about deploying activities, see "Defining a Business Activity" in *Information Workers Users Guide*.  
  
 The following table describes the values you can use for OnlineWindowTimeUnit and OnlineWindowTimeLength.  
  
|Property|Value|  
|--------------|-----------|  
|OnlineWindowTimeUnit|This property can be: month, day, hour, or minute. The default value of this property is month.|  
|OnlineWindowTimeLength|This property must be an integer. The default value of this property is 6.|  
  
 BAM moves data out of the BAM primary import database by partition, when the partition is older than the online window (current time - OnlineWindowTimeLength of OnlineWindowTimeUnit). For example, for OnlineWindowTimeLength = 5 and OnlineWindowTimeUnit = day, partitions older than 5 days are removed.  
  
 BAM moves archived activity instance data into the BAM archiving database. You specify the BAM archiving database during BizTalk BAM Configuration. For information about BizTalk BAM configuration, see [BAM Configuration Schema](../core/bam-configuration-schema.md).  
  
 BAM will not archive activity instance data if you have not run the BAM cube update Data Transformation Services (DTS) package, which processes the instance data into the activity cube.  
  
 For information about running the BAM data maintenance DTS package, see [BAM DTS Packages](../core/bam-dts-packages.md).  
  
 Over time the BAMArchive database will grow in size as activity instance data is added. Although there is no straightforward way to truncate an entire database, you can periodically truncate the database transaction log to reduce the storage requirements, and you can periodically back up and archive the entire BAMArchive database. See “Truncating the transaction log” in SQL Server Books Online for more information.  
  
## See Also  
 [Defining the Time Window and Time Slice Properties](../core/defining-the-time-window-and-time-slice-properties.md)   
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)