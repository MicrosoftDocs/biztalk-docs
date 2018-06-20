---
title: "How to List Subscribers to an Alert | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "alerts, listing subscribers"
  - "managing [BAM], listing alert subscribers"
  - "subscriptions, listing subscribers"
ms.assetid: 760cc88f-896d-43a3-a4af-b2a836190276
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to List Subscribers to an Alert
Administrators use the **get-subscriptions** command to list all of the subscribers to a specified alert.  
  
### To list subscribers to an alert  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3. Type **bm get-subscriptions -View:\<view name\> -Alert:\<alert name\>**.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
4. Press **ENTER**.  
  
## See Also  
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM Management Utility](../core/bam-management-utility.md)