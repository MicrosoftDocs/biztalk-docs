---
title: "How to Create an Index | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Create-Index command [BAM]"
  - "indexes [BAM], creating"
  - "indexes [BAM], aggregations"
  - "creating, indexes [BAM]"
  - "aggregations [BAM], indexes"
ms.assetid: 456d94e6-2e84-4d12-ad38-49f9eeb103f3
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create an Index
Administrators use the **create-index** command to create an index on the specified activity at the specified checkpoints.  
  
### To create an index on an activity  
  
1. From a command prompt, browse to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
2. Type **bm create-index -IndexName:\<index name\> -Activity:\<activity name\> -Checkpoint:\<checkpoint1\>**.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
3. Press **ENTER**.  
  
## See Also  
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM Management Utility](../core/bam-management-utility.md)   
 [How to Delete an Index](../core/how-to-delete-an-index.md)   
 [How to Get a List of Indexes on an Aggregation](../core/how-to-get-a-list-of-indexes-on-an-aggregation.md)