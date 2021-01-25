---
description: "Learn more about: Windows Groups and User Accounts in BizTalk Server"
title: "Windows Groups and User Accounts in BizTalk Server | Microsoft Docs"
ms.custom: "biztalk-2020"
ms.date: "01/14/2020"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a01603bd-4105-4691-819d-de43b00b40f3
caps.latest.revision: 25
author: "MandiOhlinger"
ms.author: "mandia"
manager: "dougeby"
---

# Windows Groups and User Accounts in BizTalk Server

Information about BizTalk Server local and domain group and user accounts. The Configuration Manager creates the necessary BizTalk group accounts for you by default if you install BizTalk Server and all prerequisite software on a single computer. The information contained in this section applies to multiple computer topologies.  
  
> [!IMPORTANT]
>  BizTalk Server supports local group and user accounts only in single computer configurations. BizTalk Server supports domain group and user accounts in both single and multiple computer configurations. If you use domain groups for your BizTalk Server configuration, you must manually create the groups before you configure BizTalk Server. The Configuration Manager cannot create domain groups.  

## Prerequisites

Have permissions to use **Active Directory Users and Computers**, and create domain groups. In most organizations, this task is done by domain administrators, not the BizTalk Server administrators.

## Create groups and user accounts

1. Open **Active Directory Users and Computers**.
2. Create the groups. For the specific steps to create on-premises groups, see [Create a Group Account in Active Directory](https://docs.microsoft.com/windows/security/threat-protection/windows-firewall/create-a-group-account-in-active-directory).

## Group list and descriptions

### SSO Administrators

Administrators of the Enterprise Single Sign-On (SSO) service.

**Group membership**:

- Includes service accounts for Enterprise Single Sign-On service.
- Includes users/groups that need to be able to configure and administer BizTalk Server and SSO service.
- Includes accounts used to run BizTalk Configuration Manager when configuring SSO master secret server.

**SQL Server roles or Database roles**:

- db_owner SQL Server database role for the SSO
- securityadmin SQL Server role for the SQL Server where SSO is located

### SSO Affiliate Administrators

Administrators of certain SSO affiliate applications. Can create/delete SSO affiliate applications, administer user mappings, and set credentials for affiliate application users

**Group membership**:

- Doesn't have any service accounts.
- Includes account used for BizTalk Server Administrators.

**SQL Server roles or database roles**: None

### BizTalk Server Administrators

Has the least privileges necessary to perform administrative tasks. Users in this group can deploy solutions, manage applications, and resolve message processing issues.

To run administrative tasks for adapters, receive and send handlers, and receive locations, the BizTalk Server Administrators must be added to the Single Sign-On Affiliate Administrators.

For more information, see [Managing BizTalk Server Security](../core/managing-biztalk-server-security.md).

**Group membership**:

Includes users and groups that need to configure and administer BizTalk Server.

**SQL Server roles or database roles**:

- BTS_ADMIN_USERS SQL Server database role in the following databases:

  - BizTalkMgmtDb
  - BizTalkMsgBoxDb
  - BizTalkRuleEngineDb
  - BizTalkDTADb
  - BAMPrimaryImport

- db_owner SQL Server database role for the following databases:

  - BAMStarSchema
  - BAMPrimaryImport
  - BAMArchive
  - BAMAlertsApplication
  - BAMAlertsNSMain

- NSAdmin SQL Server database role in the following databases:

  - BAMAlertsApplication
  - BAMAlertsNSMain

- OLAP Administrators on the computer hosting the BAMAnalysis OLAP database.

### BizTalk Server Operators

A low privilege role with access only to monitoring and troubleshooting actions.

For more information, see [Managing BizTalk Server Security](../core/managing-biztalk-server-security.md).

**Group membership**:

- Includes users or groups that monitor solutions.
- Doesn't have any service accounts.

**SQL Server roles or database roles**:

- BTS_OPERATORS SQL Server database role in the following databases:
  - BizTalkDTADb
  - BizTalkMgmtDb
  - BizTalkMsgBoxDb
  - BizTalkRuleEngineDb

### BizTalk Server Read Only Users

Has least privilege to view BizTalk Artifacts, Service State, Message Flow and Tracking Information.

For more information, see [Managing BizTalk Server Security](../core/managing-biztalk-server-security.md).

**Group membership**:

- Includes users or groups that have read permission for dev ops scenarios.
- Doesn't have any service accounts.

**SQL Server roles or database roles**:

- BTS_READONLY_USERS SQL Server database role in the following databases:
  - BizTalkMgmtDb
  - BizTalkMsgBoxDb
  - BizTalkDTADb
  - BizTalkRuleEngineDb
  - BAMPrimaryImport

### BizTalk Application Users

The default name of the first In-Process BizTalk Host Group created by Configuration Manager. Use one BizTalk host group for each in-process host in your environment. Also includes accounts with access to in-process BizTalk hosts, such as hosts processes in BizTalk Server, and BTSNTSvc.exe.

**Group membership**:

- Includes service accounts for the BizTalk In-Process host instance.
- Includes service accounts for BizTalk Rule Engine service in the host(s) that the BizTalk host group is designated for.

**SQL Server roles or database roles**:

- BTS_HOST_USERS SQL Server database role in the following databases:
  - BizTalkMgmtDb
  - BizTalkMsgBoxDb
  - BizTalkRuleEngineDb
  - BizTalkDTADb
  - BAMPrimaryImport

- BAM_EVENT_WRITER SQL Server database role in the BAMPrimaryImport

### BizTalk Isolated Host Users

The default name of the first Isolated BizTalk Host Group created by Configuration Manager. Isolated BizTalk hosts not running on BizTalk Server, such as HTTP and SOAP.

Use one BizTalk Isolated Host Group for each Isolated Host in your environment.

**Group membership**:

- Includes service accounts for the BizTalk Isolated host instance in the host that the Isolated BizTalk Host Group is designated for.

**SQL Server roles or database roles**:

BTS_HOST_USERS SQL Server database role in the following databases:

- BizTalkMgmtDb
- BizTalkMsgBoxDb
- BizTalkRuleEngineDb
- BizTalkDTADb
- BAMPrimaryImport

### BAM Portal Users

Has access to BAM Portal web site.

**Group membership**:

- Everyone group is used for this role by default.
- Doesn't have any service accounts.

**SQL Server roles or database roles**: None

### BizTalk SharePoint Adapter Enabled Hosts

Has access to Windows SharePoint Services Adapter Web Service.

**Group membership**:

- Includes service accounts for the BizTalk host instance to call the SharePoint adapter.

**SQL Server roles or database roles**: None

### BizTalk B2B Operators Group

A BizTalk role that reduces the onus on the Administrators to perform all party management operation. This role allows Windows users associated with the role to run all party management operations.

**Group membership**:

- Includes users or groups that configure and administer BizTalk Server TPM data and monitor solutions.

**SQL Server roles or database roles**:

BTS_OPERATORS SQL Server database role in the following databases:

- BizTalkDTADb
- BizTalkMgmtDb
- BizTalkMsgBoxDb
- BizTalkRuleEngineDb
- BAMPrimaryImport

## User and service accounts

The following list describes the Windows user or service accounts, and group affiliations used by BizTalk Server. It also identifies the SQL Server roles or database roles for the accounts.  

### Enterprise Single Sign-On Service

Service account used to run Enterprise Single Sign-On Service that accesses the SSO database.

**Group affiliation**:

- SSO Administrators

**SQL Server roles or database roles**: None

### BizTalk Host Instance Account

Service account used to run BizTalk In-Process host instance that accesses the In-Process BizTalk host instance (BTNTSVC).

**Group affiliation**:

- BizTalk Application Users
- SSO Affiliate Administrators

**SQL Server roles or database roles**: None

### BizTalk Isolated Host Instance Account

Service account used to run BizTalk Isolated host instance (HTTP/SOAP).

**Group affiliation**:

- BizTalk Isolated Host Users
- SSO Affiliate Administrators
- IIS_WPG

**SQL Server roles or database roles**: None

### Rule Engine Update Service

Service account that runs Rule Engine Update Service. This service receives notifications to deployment/undeployment policies from the Rule engine database.

**Group affiliation**: None

**SQL Server roles or database roles**:

- RE_HOST_USERS SQL Server database role in the BizTalkRuleEngineDb

### BAM Notification Services User

Service account that runs the BAM Notification Services. These services access the BAM databases.

**Group affiliation**:

- SQLServer2008NotificationServicesUser$\<**ComputerName**\>

**SQL Server roles or database roles**:

- NSRunService SQL Server Database Role in the following databases:
  - BAMAlertsApplication
  - BAMAlertsNSMain

- BAM_ManagementNSReader SQL Server role for the BAMPrimaryImport

### BAM Management Web Service User

User account for BAM Management Web service (BAMManagementService) to access various BAM resources. BAM Portal calls the BAMManagementService with the user credentials logged on the BAM Portal to manage alerts, get BAM definition XML and BAM views.

**Group affiliation**:

- IIS_WPG

**SQL Server roles or database roles**:

- NSSubscriberAdmin SQL Server Database Role in the following databases:
  - BAMAlertsApplication
  - BAMAlertsNSMain
- BAM_ManagementWS SQL Server role for the BAMPrimaryImport

### BAM Application Pool Account

Application pool account for BAMAppPool that hosts BAM Portal Web site.

**Group affiliation**:

- IIS_WPG

**SQL Server roles or database roles**: None

## Next steps
  
-   [Local Groups](../core/local-groups.md)  
  
-   [Domain Groups](../core/domain-groups.md)
