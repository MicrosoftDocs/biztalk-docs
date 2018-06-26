---
title: "How to Remove Subscribers from an Alert | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "subscriptions, subscribers"
  - "managing [BAM], deleting alert subscibers"
  - "alerts, subscribers"
ms.assetid: d5571863-26e3-4c1b-991f-538cd1fef347
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Remove Subscribers from an Alert
Administrators use the **remove-subscription** command to remove the specified user as a subscriber from an alert.  
  
### To remove subscribers from an alert  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3. Type **bm remove-subscription -View:\<view name\> -Alert:\<alert name\> -AccountName:\<account name\>**.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
4. Press **ENTER**.  
  
## See Also  
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM Management Utility](../core/bam-management-utility.md)   
 [How to Add Subscribers to an Alert](../core/how-to-add-subscribers-to-an-alert.md)