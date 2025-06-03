---
description: "Learn more about: How to Remove BAM Views"
title: "How to Remove BAM Views"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Remove BAM Views
Administrators use the **remove-view** command to remove a view from the BAM Primary Import database.  
  
> [!NOTE]
>  When you remove a view, you also automatically remove any alerts defined for that view.  
  
### To remove BAM views  
  
1.  Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2.  Navigate to the tracking folder by typing **C:\Program Files\Microsoft BizTalk Server 2009\Tracking** at the command prompt. Press **ENTER**.  
  
3.  Type **bm remove-view -Name:\<view name\>**.  
  
4.  Press **ENTER**.  
  
## See Also  
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM Security Recommendations](../core/bam-security-recommendations.md)   
 [BAM Management Utility](../core/bam-management-utility.md)   
 [How to Remove BAM Alerts](../core/how-to-remove-bam-alerts.md)
