---
title: "How to Delete an Index | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "indexes [BAM], deleting"
  - "Get-Index command [BAM]"
  - "aggregations [BAM], indexes"
ms.assetid: 5f9c7989-3357-451f-8565-1d4b01c1d16a
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Delete an Index
Administrators use the **delete-index** command to delete an index on the specified activity at the specified checkpoints.  
  
### To delete an index on an activity  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt. Press **ENTER**.  
  
3. Type **bm delete-index -IndexName:\<index name\> -Activity:\<activity name\>**.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
4. Press **ENTER**.  
  
## See Also  
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM Management Utility](../core/bam-management-utility.md)   
 [How to Delete an Index](../core/how-to-delete-an-index.md)   
 [How to Get a List of Indexes on an Aggregation](../core/how-to-get-a-list-of-indexes-on-an-aggregation.md)