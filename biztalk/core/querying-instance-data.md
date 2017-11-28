---
title: "Querying Instance Data | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BAM, instance data"
  - "queries [BAM], instance data"
ms.assetid: ae4a8854-d5c2-4b36-a0ef-3f74e138306e
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Querying Instance Data
The data about individual activity instances is available for queries in a dynamically created SQL View in the BAM Primary Import Database.  
  
 The name of this view is  
  
 **bam_\<** *ViewName* **\>_\<** *ActivityName* **\>_View**  
  
 Where  
  
 **\<** *ViewName* **\>** is the Name Attribute of the View element in the BAM Definition XML, which is the same as the View Name entered in the related Microsoft Excel wizards.  
  
 **\<** *ActivityName* **\>** is the Name Attribute of the Activity element in the BAM Definition XML, which is the same as the Activity Name entered in the Excel wizards.  
  
 It is important to note the following conditions when querying instance data:  
  
-   If you send activity data to BAM via the DirectEventStream, the instance data has no latency, meaning that it appears instantaneously when the transaction in the calling application commits.  
  
-   If the activity data is sent to BAM via the BufferedEventStream, the instance data will show up for queries a few seconds later, depending on the load of the BAM Event Bus service and the SQL server that hosts the BAM Primary Import Database.  
  
-   The actual structure of tables behind this view is more complex to ensure that the data for the current or recent activities is available for queries, while data for activities that have completed and is no longer required for active queries is archived or purged without taking the system offline. For more information, see [Activity Data Storage](../core/activity-data-storage.md).  
  
## See Also  
 [Activity Data Storage](../core/activity-data-storage.md)   
 [Querying BAM Data](../core/querying-bam-data.md)