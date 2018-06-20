---
title: "Windows Groups and User Accounts in BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Tracking database, BTS_ADMIN_USERS role [SQL Server database]"
  - "MessageBox database, BTS_HOST_USERS role [SQL Server database]"
  - "Rule Engine database, BTS_HOST_USERS role [SQL Server database]"
  - "Management database, BTS_OPERATORS role [SQL Server database]"
  - "BTS_HOST_USERS role [SQL Server database]"
  - "NSSubscriberAdmin role [SQL Server database]"
  - "Management database, tpm_user role [SQL Server database]"
  - "SSO, securityadmin role [SQL Server database]"
  - "IIS_WPG group"
  - "BAM Notification service account"
  - "EDI_ADMIN_USERS role [SQL Server database]"
  - "Archive database [BAM], db_owner role [SQL Server database]"
  - "Primary Import database [BAM], db_owner role [SQL Server database]"
  - "Primary Import database [BAM], BAM_EVENT_WRITER role [SQL Server database]"
  - "Notification Services Application database [BAM], db_owner role [SQL Server database]"
  - "NSRunService role [SQL Server database]"
  - "RE_HOST_USERS role [SQL Server database]"
  - "MessageBox database, BTS_OPERATORS role [SQL Server database]"
  - "Rule Engine database, RE_HOST_USERS role [SQL Server database]"
  - "Windows groups, creating"
  - "securityadmin role [SQL Server database]"
  - "BizTalk Isolated Host Instance service account"
  - "In-Process BizTalk Host groups"
  - "Primary Import database [BAM], BTS_ADMIN_USERS role [SQL Server database]"
  - "SSO Affiliate Administrators [Windows group]"
  - "Star Schema database [BAM], db_owner role [SQL Server database]"
  - "Notification Services Instance database [BAM], db_owner role [SQL Server database]"
  - "MessageBox database, BTS_ADMIN_USERS role [SQL Server database]"
  - "Rule Engine Update Service account"
  - "Configuration Manager, creating user accounts"
  - "SSO Administrators [Windows group]"
  - "Rule Engine database, BTS_ADMIN_USERS role [SQL Server database]"
  - "Tracking database, BTS_OPERATORS role [SQL Server database]"
  - "Primary Import database [BAM], BAM_ManagementNSReader role [SQL Server database]"
  - "Notification Services Instance database [BAM], role [SQL Server database]"
  - "BizTalk Application Users [Windows group]"
  - "user accounts, creating"
  - "Rule Engine database, BTS_OPERATORS role [SQL Server database]"
  - "STS_WPG group"
  - "BAM_ManagementWS role [SQL Server database]"
  - "BTS_OPERATORS role [SQL Server database]"
  - "Tracking database, BTS_HOST_USERS role [SQL Server database]"
  - "SSO, db_owner role [SQL Server database]"
  - "Notification Services Application database [BAM], role [SQL Server database]"
  - "OLAP Administrators"
  - "BAM_EVENT_WRITER role [SQL Server database]"
  - "Windows groups, group list"
  - "tpm_user role [SQL Server database]"
  - "BizTalk Host Instance service account"
  - "Base DBI database, EDI_ADMIN_USERS role [SQL Server database]"
  - "Primary Import database [BAM], role [SQL Server database]"
  - "BizTalk SharePoint Adapter Enabled Hosts [Windows group]"
  - "BAM Management Web service account"
  - "db_owner role [SQL Server database]"
  - "Management database, BTS_ADMIN_USERS role [SQL Server database]"
  - "Configuration Manager, creating groups"
  - "Management database, BTS_HOST_USERS role [SQL Server database]"
  - "BizTalk Server Operators [Windows group]"
  - "Base DBI database, BTS_OPERATORS role [SQL Server database]"
  - "Enterprise Single Sign-On Service account"
  - "NSAdmin role [SQL Server database]"
  - "BAM_ManagementNSReader role [SQL Server database]"
  - "Notification Services Application database [BAM], NSRunService role [SQL Server database]"
  - "BTS_ADMIN_USERS role [SQL Server database]"
  - "BizTalk Isolated Host Users [Windows group]"
  - "Notification Services Instance database [BAM], NSAdmin role [SQL Server database]"
  - "SQLServer2005NotificationServicesUser"
  - "EDI Subsystem Users [Windows group]"
  - "Primary Import database [BAM], BTS_HOST_USERS role [SQL Server database]"
  - "BizTalk Server Administrators [Windows group]"
  - "BAM Portal Users [Windows group]"
  - "Notification Services Application database [BAM], NSAdmin role [SQL Server database]"
ms.assetid: a01603bd-4105-4691-819d-de43b00b40f3
caps.latest.revision: 25
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Windows Groups and User Accounts in BizTalk Server
Information about BizTalk Server local and domain group and user accounts. The Configuration Manager creates the necessary BizTalk group accounts for you by default if you install BizTalk Server and all prerequisite software on a single computer. The information contained in this section applies to multiple computer topologies.  
  
> [!IMPORTANT]
>  BizTalk Server supports local group and user accounts only in single computer configurations. BizTalk Server supports domain group and user accounts in both single and multiple computer configurations. If you use domain groups for your BizTalk Server configuration, you must manually create the groups before you configure BizTalk Server. The Configuration Manager cannot create domain groups.  
  
## Procedures  
  
#### To create Windows Group and User Accounts in BizTalk Server  
  
1. Using Active Directory, from the **Start** menu, point to **Programs**, point to **Administrative Tools**, and select **Active Directory Users and Computers**.  
  
2. In the Active Directory Users and Computers window, right-click at the bottom of the right pane, or right-click the **Users** folder in the navigation tree in the left pane.  
  
3. Select **New**, then select **Group** or **User**.  
  
4. Enter the group or user information outlined in the following table.  
  
   The following table lists the Windows group and their membership used by BizTalk Server. It also identifies the SQL Server Roles or Database Roles for the group.  
  
|Group|Group Description|Membership|SQL Server Roles or Database Roles|  
|-----------|-----------------------|----------------|----------------------------------------|  
|SSO Administrators|Administrator of the Enterprise Single Sign-On (SSO) service.|Contains service accounts for Enterprise Single Sign-On service.<br /><br /> Contains users/groups that need to be able to configure and administer BizTalk Server and SSO service.<br /><br /> Contains accounts used to run BizTalk Configuration Manager when configuring SSO master secret server.|db_owner SQL Server Database Role for the SSO<br /><br /> securityadmin SQL Server Role for the SQL Server where SSO is located|  
|SSO Affiliate Administrators|Administrators of certain SSO affiliate applications.<br /><br /> Can create/delete SSO affiliate applications, administer user mappings, and set credentials for affiliate application users|Contains no service accounts.<br /><br /> Contains account used for BizTalk Server Administrators.||  
|BizTalk Server Administrators|Has the least privileges necessary to perform administrative tasks<br /><br /> Can deploy solutions, manage applications, and resolve message processing issues.<br /><br /> To perform administrative tasks for adapters, receive and send handlers, and receive locations, the BizTalk Server Administrators must be added to the Single Sign-On Affiliate Administrators.<br /><br /> For more information, see [Managing BizTalk Server Security](../core/managing-biztalk-server-security.md).|Contains users/groups that need to be able to configure and administer BizTalk Server.|BTS_ADMIN_USERS SQL Server Database Role in the following databases:<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb<br /><br /> BizTalkDTADb<br /><br /> BAMPrimaryImport<br /><br /> db_owner SQL Server Database Role for the following databases:<br /><br /> BAMStarSchema<br /><br /> BAMPrimaryImport<br /><br /> BAMArchive<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> NSAdmin SQL Server Database Role in the following databases:<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> OLAP Administrators on the computer hosting the BAMAnalysis OLAP database.|  
|BizTalk Server Operators|Has a low privilege role with access only to monitoring and troubleshooting actions<br /><br /> For more information, see [Managing BizTalk Server Security](../core/managing-biztalk-server-security.md)|Contains user/groups that will monitor solutions.<br /><br /> Contains no service accounts.|BTS_OPERATORS SQL Server Database Role in the following databases:<br /><br /> BizTalkDTADb<br /><br /> BizTalkEDIDb<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb|  
|BizTalk Application Users|The default name of the first In-Process BizTalk Host Group created by Configuration Manager.<br /><br /> Use one BizTalk Host Group for each In-Process host in your environment.<br /><br /> Includes accounts with access to In-Process BizTalk Hosts (hosts processes in BizTalk Server, BTSNTSvc.exe).|Contains service accounts for the BizTalk In-Process host instance in the host that the BizTalk Host Group is designated for.|BTS_HOST_USERS SQL Server Database Role in the following databases:<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb<br /><br /> BizTalkDTADb<br /><br /> BAMPrimaryImport<br /><br /> BAM_EVENT_WRITER SQL Server Database Role in the BAMPrimaryImport|  
|BizTalk Isolated Host Users|The default name of the first Isolated BizTalk Host Group created by Configuration Manager. Isolated BizTalk hosts not running on BizTalk Server, such as HTTP and SOAP.<br /><br /> Use one BizTalk Isolated Host Group for each Isolated Host in your environment.|Contains service accounts for the BizTalk Isolated host instance in the host that the Isolated BizTalk Host Group is designated for.|BTS_HOST_USERS SQL Server Database Role in the following databases:<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb<br /><br /> BizTalkDTADb<br /><br /> BAMPrimaryImport|  
|BAM Portal Users|Has access to BAM Portal Web site.|Everyone group is used for this role by default.<br /><br /> Contains no service accounts.||  
|BizTalk SharePoint Adapter Enabled Hosts|Has access to Windows SharePoint Services Adapter Web Service|Contains service accounts for the BizTalk host instance to be able to call SharePoint Adapter.||  
|BizTalk B2B Operators Group|A new BizTalk role that reduces the onus on the Administrators to perform all Party management operation. This role allows windows users associated with the role to perform all party management operations.|Contains users/groups that must be able to configure and administer BizTalk Server TPM data and monitor solutions.|BTS_OPERATORS SQL Server Database Role in the following databases: BizTalkDTADb, BizTalkMgmtDb, BizTalkMsgBoxDb, BizTalkRuleEngineDb and BAMPrimaryImport|  
  
 The following table lists the Windows user or service accounts and group affiliations used by BizTalk Server. It also identifies the SQL Server Roles or Database Roles for the accounts.  
  
|User|User Description|Group Affiliation|SQL Server Roles or Database Roles|  
|----------|----------------------|-----------------------|----------------------------------------|  
|Enterprise Single Sign-On Service|Service account used to run Enterprise Single Sign-On Service which accesses the SSO database.|SSO Administrators||  
|BizTalk Host Instance Account|Service account used to run BizTalk In-Process host instance which access In-Process BizTalk host instance (BTNTSVC).|BizTalk Application Users<br /><br /> SSO Affiliate Administrators||  
|BizTalk Isolated Host Instance Account|Service account used to run BizTalk Isolated host instance (HTTP/SOAP).|BizTalk Isolated Host Users<br /><br /> SSO Affiliate Administrators<br /><br /> IIS_WPG||  
|Rule Engine Update Service|Service account used to run Rule Engine Update Service which receives notifications to deployment/undeployment policies from the Rule engine database.||RE_HOST_USERS SQL Server Database Role in the BizTalkRuleEngineDb|  
|BAM Notification Services User|Service account used to run BAM Notification Services which accesses the BAM databases.|SQLServer2008NotificationServicesUser$\<**ComputerName**\>|NSRunService SQL Server Database Role in the following databases:<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> BAM_ManagementNSReader SQL Server role for the BAMPrimaryImport|  
|BAM Management Web Service User|User account for BAM Management Web service (BAMManagementService) to access various BAM resources. BAM Portal calls BAMManagementService with the user credentials logged on the BAM Portal to manage alerts, get BAM definition XML and BAM views|IIS_WPG|NSSubscriberAdmin SQL Server Database Role in the following databases:<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> BAM_ManagementWS SQL Server role for the BAMPrimaryImport|  
|BAM Application Pool Account|Application pool account for BAMAppPool which hosts BAM Portal Web site.|IIS_WPG||  
  
## In This Section  
  
-   [Local Groups](../core/local-groups.md)  
  
-   [Domain Groups](../core/domain-groups.md)