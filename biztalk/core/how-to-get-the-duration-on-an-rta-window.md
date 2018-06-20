---
title: "How to Get the Duration on an RTA Window | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [BAM], aggregations"
  - "aggregations [BAM], time intervals"
  - "managing [BAM], time intervals"
  - "Get-RTAWindow command [BAM]"
ms.assetid: 4e7ad0fd-e7ed-47f7-9435-ef01bbe17afa
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Get the Duration on an RTA Window
Administrators use the **get-rtawindow** command to get the duration for the specified real-time aggregation (RTA). The command returns the length of the duration and the units by which the duration is measured.  
  
### To get the duration on an aggregation  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. Navigate to the folder [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3. Type **bm get-rtawindow -View:\<view name\> -Activity:\<activity name\> -Rta:\<RTA name\>**.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
4. Press **ENTER**.  
  
## See Also  
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM Management Utility](../core/bam-management-utility.md)   
 [How to Set the Duration on an RTA Window](../core/how-to-set-the-duration-on-an-rta-window.md)