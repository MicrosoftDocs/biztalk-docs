---
title: "Minimum Security User Rights | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "security, user accounts"
  - "permissions, user accounts"
  - "permissions, roles"
  - "administrator accounts, permissions"
  - "roles, permissions"
  - "permissions, administrator accounts"
  - "user accounts, permissions"
  - "user accounts, access control"
  - "security, permissions"
ms.assetid: 44b6e7da-8e6c-40c0-a250-52ab422c0adf
caps.latest.revision: 25
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Minimum Security User Rights
The groups and accounts that BizTalk Server uses have the minimum user rights they need to perform most tasks. Therefore, there are some tasks where you may need more user rights than the ones BizTalk Server automatically has granted the group to which you belong. In this topic:  
  
 [Group and Role Membership](../core/minimum-security-user-rights.md#BKMK_GroupRole)  
  
 [User rights for performing administrative tasks](../core/minimum-security-user-rights.md#BKMK_UserRights)  
  
 [Community Addition – Task List](../core/minimum-security-user-rights.md#BKMK_Community)  
  
##  <a name="BKMK_GroupRole"></a> Group and Role Membership  
 The following table describes the Minimum Security User Rights you need to perform tasks in BizTalk Server:  
  
|Task|Groups or Roles|  
|----------|---------------------|  
|**Setup**||  
|Installation|-   Local Administrators|  
|Configuration|-   BizTalk Server Administrators<br />-   Local Administrators<br />-   sysadmin SQL Server Role<br />-   SSO Administrators<br />-   OLAP Administrator|  
|Join a BizTalk Server group|-   Local Administrators<br />-   BizTalk Server Administrators|  
|**BizTalk Administration**||  
|Create a MessageBox database|-   BizTalk Server Administrators<br />-   sysadmin SQL Server Role|  
|Create or delete a BizTalk host|-   BizTalk Server Administrators<br />-   db_ddladmin SQL Server Database role on the BizTalk MessageBox databases|  
|Change the Host Tracking property for a host|-   BizTalk Server Administrators<br />-   db_securityadmin SQL Server Database role on the BAM Primary Import database, BizTalk MessageBox databases, and the BizTalk Tracking database|  
|Create (install), delete, or change the credentials for a host instance|<ul><li>BizTalk Server Administrators</li><li>Local Administrators</li><li>securityadmin SQL Server Role on the server(s) where the following databases are:<br /><br /> <ul><li>BizTalk MessageBox databases, BizTalk Management database, Rule Engine database, BizTalk Tracking database, BAM Primary Import database</li></ul></li><li>db_securityadmin SQL Server Database role on the following databases:<br /><br /> <ul><li>BizTalk MessageBox databases, BizTalk Management database, Rule Engine database, BizTalk Tracking database, BAM Primary Import database</li></ul></li></ul>|  
|Start or stop a host instance|-   BizTalk Server Administrators|  
|Add or remove Server|-   BizTalk Server Administrators<br />-   Local Administrators on the computer you are adding or removing.|  
|Add or remove a receive handler|-   BizTalk Server Administrators<br />-   SSO Affiliate administrators|  
|Start or stop applications, orchestrations, send ports, and send port groups|-   BizTalk Server Operators|  
|Enable or disable receive locations|-   BizTalk Server Operators|  
|Search for artifacts|-   BizTalk Server Operators|  
|Add an adapter|-   BizTalk Server Administrators<br />-   SSO Affiliate administrators|  
|Backup databases|-   BTS_BACKUP_USERS role for the databases<br />-   sysadmin SQL Server role on the SQL Server hosting BizTalk Management database. **Note:**  You must configure the SQL Server Agent service to run under a domain account or a local account with a mapped user on each instance of SQL Server.|  
|Configure BizTalk Groups with a certificate|-   BizTalk Server Administrators|  
|All other tasks (including WMI)|-   BizTalk Server Administrators|  
|**Operations and  Message and Service Instance Tracking**||  
|View Group Hub page, perform queries, save and load queries|-   BizTalk Server Operators|  
|View query results|-   BizTalk Server Operators|  
|General configuration and tracking configuration|-   BizTalk Server Administrators (read and write)<br />-   BizTalk Server Operators (read)|  
|Browse a health monitoring cube|-   BizTalk Server Administrators|  
|View message properties|-   BizTalk Server Administrators|  
|Save message bodies|-   BizTalk Server Administrators|  
|Use **Find Message** query|-   BizTalk Server Administrators|  
|Use **Query Build**|-   BizTalk Server Administrators|  
|Use the orchestration debugger|-   BizTalk Server Administrators|  
|View message flow, message events in the Group Hub page using the BizTalk Server Administration console.|-   BizTalk Server Operators|  
|Suspend, terminate, or resume instances|-   BizTalk Server Operators|  
|Archiving or purging messages from the Tracking database|-   db_owner role on the BizTalk Tracking database|  
|All other tasks|-   BizTalk Server Administrators|  
|**Tracking Profile Editor**||  
|Read or write to the BizTalk Management database|-   BizTalk Server Administrators|  
|**Event Bus Monitoring MMC**||  
|All tasks|-   BizTalk Server Administrators|  
|**BizTalk WCF Service Publishing Wizard**||  
|All tasks|-   Local Administrators|  
|**BizTalk Web Services Publishing Wizard**||  
|All tasks|-   Local Administrators|  
|**Business Activity Monitoring**||  
|Run BM.exe|-   db_owner SQL Server Database role in the BAM Primary Import, BAM Star Schema, and BAM Archive databases|  
|Run BM.exe, if there is an Analysis Services database|-   db_owner SQL Server Database role in the BAM Primary Import, BAM Star Schema, and BAM Archive databases<br />-   OLAP Administrators in the BAM Analysis Services database|  
|Create account for BAM View|-   db_owner SQL Server Database role in the BAM Primary Import database<br />-   OLAP Administrators in the BAM Analysis Services database|  
|**Rule Engine (publishing rules)**||  
|Deploy/undeploy policies, manipulate security-related artifacts|-   RE_ADMIN_USERS SQL Server Database role in the Rule engine database|  
  
##  <a name="BKMK_UserRights"></a> User rights for performing administrative tasks  
 In order to perform administrative tasks, using either the BizTalk Server Administration Console or Windows Management Instrumentation (WMI), the account performing the administrative tasks requires different levels of user rights depending on the task to perform.  
  
 The following table describes the user rights the account needs to perform the tasks, from least user rights (level 1), to most user rights (level 4).  
  
|Level of user rights|User rights granted|Tasks|  
|--------------------------|-------------------------|-----------|  
|0|-   BizTalk Server Operators|-   Basic administration and monitoring tasks. No ability to change configuration settings. No access to message properties or content.|  
|1|-   BizTalk Server Administrators|-   All administrative tasks, except the ones that require level 2-4 user rights|  
|2|-   User rights granted to level 1<br />-   securityadmin SQL Server role on all SQL Servers<br />-   db_securityadmin and db_accessadmin SQL Server Database roles in the BizTalk Tracking, Rule Engine, BizTalk Management, BAM Primary Import and BizTalk MessageBox databases<br />-   db_ddladmin SQL Server Database role on all BizTalk MessageBox databases<br />-   SSO Affiliate administrators|-   Create and delete BizTalk hosts<br />-   Change host tracking property<br />-   Add and delete servers<br />-   Add and delete receive handlers<br />-   Add adapters|  
|3|-   User rights granted to level 2<br />-   Local Administrators on all BizTalk Server runtime computers|-   Create and delete host instances|  
|4|-   User rights granted to level 3<br />-   sysadmin SQL Server role on all of the SQL Servers that have BizTalk MessageBox databases|-   Create MessageBox databases|  
  
##  <a name="BKMK_Community"></a> Community Addition – Task List  
 [Minimum Security Rights for BizTalk Server 2013 R2](http://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2013-r2.aspx) (http://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2013-r2.aspx)  
  
## See Also  
 [Access Control and Data Security](../core/access-control-and-data-security.md)   
 [Designing the System Architectures for BizTalk Server](../core/designing-the-system-architectures-for-biztalk-server.md)   
 [Databases in BizTalk Server](../core/databases-in-biztalk-server.md)   
 [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)