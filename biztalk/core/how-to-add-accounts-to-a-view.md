---
title: "How to Add Accounts to a View | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Excel add-in [BAM], security"
  - "Add-Account command [BAM]"
  - "managing [BAM], adding accounts to views"
ms.assetid: 0875796c-82a4-4165-9bed-88e8ba466548
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add Accounts to a View
Administrators use the **add-account** command to associate users with BAM views and protect BAM Excel Spreadsheet views from unauthorized access. When users save BAM views, the views reference a SQL connection string that is hidden within the workbook. The workbook is protected, but you must ensure that the document is protected.  
  
 When you associate users with BAM views, you restrict access to the views to only the users or groups to whom you grant access.  
  
> [!IMPORTANT]
>  If you are using real-time aggregations (RTAs), users added with **add-account** are not automatically granted logon rights to the computer running SQL Server. If you are using RTAs, consider establishing a Windows user group that contains all of the users that need to see views of the RTAs. Grant that group explicit SQL Server logon rights on the SQL server hosting the BAM Primary Import database.  
  
 For information about viewing BAM views, see [How to List BAM Views](../core/how-to-list-bam-views.md).  
  
### To add an account to a view  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt. Press **ENTER**.  
  
3. Type **bm add-account -AccountName:\<account name\> -View:\<view name\>**.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
4. Press **ENTER**.  
  
## See Also  
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM Management Utility](../core/bam-management-utility.md)