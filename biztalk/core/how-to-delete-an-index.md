---
description: "Learn more about: How to Delete an Index"
title: "How to Delete an Index"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
