---
title: "How to Disable a BAM Primary Import Database Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 78d2d644-6ebb-4051-ae59-af7d0fb75753
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Disable a BAM Primary Import Database Reference
Administrators use the **disable-reference** command to disable a reference to a specified BAM Primary Import database.  
  
### To disable a reference to a BAM Primary Import database  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3. Type the following at the command line prompt: **bm disable-reference -TargetServer:\<target server\> -TargetDatabase:\<target database\>[ -Server:\<server\> ][ -Database:\<database\> ]**, where **\<**<em>target server</em>**\>** is replaced by the name of the SQL server on which the target BAM Primary Import database specified by \<*target database*\> resides. Press **ENTER**.  
  
## See Also  
 [BAM Management Utility](../core/bam-management-utility.md)