---
description: "Learn more about: How to Disable a BAM Primary Import Database Reference"
title: "How to Disable a BAM Primary Import Database Reference"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Disable a BAM Primary Import Database Reference
Administrators use the **disable-reference** command to disable a reference to a specified BAM Primary Import database.  
  
### To disable a reference to a BAM Primary Import database  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3. Type the following at the command line prompt: **bm disable-reference -TargetServer:\<target server\> -TargetDatabase:\<target database\>[ -Server:\<server\> ][ -Database:\<database\> ]**, where **\<**<em>target server</em>**\>** is replaced by the name of the SQL server on which the target BAM Primary Import database specified by \<*target database*\> resides. Press **ENTER**.  
  
## See Also  
 [BAM Management Utility](../core/bam-management-utility.md)
