---
title: "How to Remove BAM Views | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BAM, views"
  - "managing [BAM definitions], deleting views"
  - "Remove-View command [BAM]"
ms.assetid: 1a43ec81-20b1-41f7-941f-753132ac9ed2
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Remove BAM Views
Administrators use the **remove-view** command to remove a view from the BAM Primary Import database.  
  
> [!NOTE]
>  When you remove a view, you also automatically remove any alerts defined for that view.  
  
### To remove BAM views  
  
1.  Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2.  Navigate to the tracking folder by typing **C:\Program Files\Microsoft BizTalk Server 2009\Tracking** at the command prompt. Press **ENTER**.  
  
3.  Type **bm remove-view -Name:\<view name>**.  
  
4.  Press **ENTER**.  
  
## See Also  
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM Security Recommendations](../core/bam-security-recommendations.md)   
 [BAM Management Utility](../core/bam-management-utility.md)   
 [How to Remove BAM Alerts](../core/how-to-remove-bam-alerts.md)