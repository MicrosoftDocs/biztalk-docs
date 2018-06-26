---
title: "How to Set Up the BAM Databases Using the BAM Management Utility | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 801338f4-b363-4f8e-b248-9c628065ded2
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Set Up the BAM Databases Using the BAM Management Utility
Administrators typically use the BizTalk Server configuration utility to set up the BAM databases. You can use the BAM Management utility (bm.exe) as an alternate method to set up the databases.  
  
## Prerequisites  
 The following are prerequisites for performing the procedure in this topic:  
  
-   You must have administrator permissions on the SQL server hosting the BAMPrimaryImport, BAMStarSchema, and BAMArchive databases.  
  
-   To set up the SQL Notification Services databases, you must have administrator permission and be a member of the local administrators group, as well as be a member of any additional administrator groups that have been configured, such as the BTS Admins group.  
  
-   You must have a BAM configuration file containing XML data from which to set up the databases.  
  
### To set up the BAM databases using the BAM Management utility  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3. Type the following at the command line prompt: **bm setup-databases -ConfigFile:\<configuration file\>**, where \<*configuration file*\> is replaced by the name of your BAM configuration file. Press **ENTER**.  
  
## See Also  
 [BAM Management Utility](../core/bam-management-utility.md)