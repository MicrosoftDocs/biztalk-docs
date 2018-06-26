---
title: "BAM Management Utility | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c55aabe2-f38b-4917-863c-b408a4eef98e
caps.latest.revision: 50
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BAM Management Utility
Administrators of Business Activity Monitoring (BAM) definitions use the BAM Management utility to manage and maintain all aspects of the BAM infrastructure.  
  
 You can use the BAM utility to perform the following tasks:  
  
-   Consume BAM definition and BAM configuration XML as input. The BAM definition XML or XLS files define the data to track and aggregate, as well as the business end user's view on the tracking data. The BAM configuration XML mandates where to deploy the infrastructure, such as the server name, database name, and other database settings.  
  
-   Deploy the run-time infrastructure on the server, which includes the BAM Primary Import database, BAM Star Schema database, BAM Analysis database, and corresponding Data Transformation Services (DTS) packages. The following items are created during this step:  
  
    -   BAM Primary Import database  
  
    -   BAM Star Schema database  
  
    -   BAM Archive database  
  
    -   BAM Analysis database  
  
> [!NOTE]
>  The locale setting of the computer running the BAM Management utility must be the same as the locale used to create the BAM definition being deployed in order for the BAM commands to work properly. For example, if you execute the **get-views** command on a computer configured with an English locale setting against a database on a computer with a French locale you will not be able to use the returned view name unless you reset your computer locale to French.  
  
 You can use the BAM Management utility to generate and deploy your tracking configuration on a server. The BAM Management utility is a command-line tool located at \<*installation path*\>\Program Files\Microsoft BizTalk Server \<version\>\Tracking\BM.exe.  
  
> [!IMPORTANT]
>  To run the BAM management utility, you must be member of the **db_owner** SQL Server Database role in the BAM Primary Import, BAM Star Schema, and BAM Archive databases. You must also have sysadmin permissions on the BAM Alerts databases if making any updates related to BAM Alerts.  
  
> [!NOTE]
>  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  
  
## BAM Management Utility Commands  
 The command descriptions use these conventions:  
  
- The square brackets ([]) indicate an optional parameter.  
  
- The angled brackets (<>) indicate a required parameter.  
  
- The braces ({}) indicate that one item should be selected from the enumerated list.  
  
- A security account can be either an NT group or an individual NT user account.  
  
- A BAM definition file can be either an XML file or a BAM Excel workbook file (.xls).  
  
- If the BAM configuration file is not supplied, it defaults to BamConfiguration.xml in the current folder.  
  
  The Individual command descriptions are contained in the following topics:  
  
- [Database Commands](../core/database-commands.md)  
  
- [Deployment of BAM Definition (Observation Model) Commands](../core/deployment-of-bam-definition-observation-model-commands.md)  
  
- [Infrastructure Management Commands](../core/infrastructure-management-commands.md)  
  
- [Activity Management Commands](../core/activity-management-commands.md)  
  
- [View Management Commands](../core/view-management-commands.md)  
  
- [Alert Management Commands](../core/alert-management-commands.md)  
  
- [User Management Commands](../core/user-management-commands.md)  
  
- [Alert Subscription Management Commands](../core/alert-subscription-management-commands.md)  
  
- [Interceptor Management Commands](../core/interceptor-management-commands.md)  
  
## Displaying the BAM Management Utility Help  
 You use the **/?** or the **help BAM Management utility** command to display the Help file for the BAM Management utility.  
  
#### To display the Help file for the BAM Management utility  
  
1.  From a command prompt, browse to the following directory: C:\Program Files\Microsoft BizTalk Server \<version\>\Tracking\\.  
  
2.  Type **bm** or **bm help**.  
  
3.  Press ENTER.