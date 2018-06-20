---
title: "How to Enable Notifications Services on Additional Computers In A Group | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 571d6b45-b0cc-47f2-bed3-7c6f3e70decc
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Enable Notifications Services on Additional Computers In A Group
When running BAM in a multi-computer environment, you must enable Notification Services on each computer on which you will run the BAM Management Utility to deploy an activity.  
  
 Consider the following scenario:  
  
- Group A consists of the following computers:  
  
  - Computer 1 is used as a BAM administration computer.  
  
  - Computer 2 hosts the BAM PIT and Star Schema database.  
  
  - Computer 3 hosts the BAM Archive and Analysis databases.  
  
  - Computer 4 hosts the BAM Alerts database.  
  
  - Computer 5 hosts the rest of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.  
  
- Group B:  
  
  -   Computer 6 is used as a BAM administration computer on which all the databases are shared with Group A.  
  
  To be able to deploy an activity to the databases in group A from the computer in group B, you must first register the Notification Services with the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] hosting the notifications services. If the Notification Services are not registered, you will receive the following error:  
  
  Deploying Alert... ERROR: The BAM deployment failed.  
  
  The alerts were not deployed.  
  
  Exception has been thrown by the target of an invocation.  
  
  The registry entries for the specified instance of Notification Services could not be found.  
  
### To register notifications services additional computers  
  
1.  On the computer in the additional group, click **Start**, point to **All Programs**, click **Microsoft SQL Server 2005**, click **Configuration Tools**, and then click **Notification Services Command Prompt**.  
  
2.  At the command prompt, type: **nscontrol register -name \<NS Prefix name chosen at config\> -server \<ns db sql server\>**. This enables Notification Services to log on to the correct database (this information is maintained in the registry of the service machine by nscontrol).  
  
## See Also  
 [Changing BAM Runtime Settings](../core/changing-bam-runtime-settings.md)   
 [BAM Management Utility](../core/bam-management-utility.md)