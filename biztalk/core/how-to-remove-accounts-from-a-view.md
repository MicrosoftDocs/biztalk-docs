---
description: "Learn more about: How to Remove Accounts from a View"
title: "How to Remove Accounts from a View"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Remove Accounts from a View
Administrators use the **remove-account** command to remove users from BAM views and protect BAM Excel Spreadsheet views from unauthorized access.  
  
 For information about viewing BAM views, see [How to List BAM Views](../core/how-to-list-bam-views.md).  
  
### To remove an account from a view  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking  
  
3. Type **bm remove-account -AccountName:\<account name\> -View:\<view name\>**.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
4. Press **ENTER**.  
  
## See Also  
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM Management Utility](../core/bam-management-utility.md)
