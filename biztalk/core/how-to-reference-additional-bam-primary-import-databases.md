---
description: "Learn more about: How to Reference Additional BAM Primary Import Databases"
title: "How to Reference Additional BAM Primary Import Databases"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Reference Additional BAM Primary Import Databases
Administrators use the **enable-reference** command to reference additional BAM Primary Import databases. You reference multiple BAM Primary Import databases to facilitate viewing distributed BAM activities.  
  
### To enable a reference to an additional BAM Primary Import database  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3. Type the following at the command line prompt: **bm enable-reference -TargetServer:\<target server\> -TargetDatabase:\<target database\>**, where \<*target server*\> is replaced by the name of the SQL server on which the target BAM Primary Import database specified by \<target database\> resides. Press ENTER.  
  
## See Also  
 [BAM Management Utility](../core/bam-management-utility.md)
