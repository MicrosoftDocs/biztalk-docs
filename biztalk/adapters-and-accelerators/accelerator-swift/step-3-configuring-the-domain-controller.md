---
title: "Step 3: Configuring the Domain Controller | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring, domain controller"
  - "domain controller"
ms.assetid: 1c513225-378b-4e57-ba29-7532b6cbcc9a
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3: Configuring the Domain Controller
This section describes how to configure the domain controller in your [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] deployment. Specifically, this section describes how to install and configure [!INCLUDE[btsAD](../../includes/btsad-md.md)] by doing the following:  
  
-   Installing Active Directory and DNS  
  
-   Creating the required accounts  
  
-   Joining the domain  
  
## Installing Active Directory and DNS  
 Use the [!INCLUDE[btsAD](../../includes/btsad-md.md)] Installation Wizard to simplify the process of configuring a domain controller. After installing Active Directory, create a Domain Name System (DNS) reverse lookup zone. Then create and add hosts to the forward and reverse lookup zones.  
  
## Creating the Required Accounts  
 The following table provides details on how to create the Global Security groups. Create the following **Global Security** groups and users on the domain controller using your own naming conventions. The examples provided below are used for simplicity. Add the specified members in the list to the created groups.  
  
 When creating groups, select **Global** for the Group Scope and **Security** for the Group Type.  
  
|Account or group name|Type|Description|Members|  
|---------------------------|----------|-----------------|-------------|  
|Admin|User|Local administrative account for all BizTalk computers, domain controller and all computers running SQL Server.<br /><br /> This is a domain user account that is used for installing applications ([!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)], and SQL Server) and for configuring BizTalk Accelerator for A4SWIFT during design time. You do not have to have domain administrator privileges to perform the A4SWIFT installation. The Admin user account must be a member of the Domain Users group, the domain BizTalk Server Administrators group, and the local Administrators group||  
|SQLSvc|User|Account for running the SQL Server service||  
|SSOSvc|User|Account for running the Single Sign-on (SSO) service||  
|HostSvc|User|Account for running the BizTalk host service||  
|IsolatedSvc|User|Account for running the BizTalk isolated service||  
|BAMSvc|User|Required for BizTalk Server configuration of BAMPortal, BAMAlerts, and BAMTools||  
|BRESvc|User|Account for running the Rule Engine Update Service service||  
|Domain Admins|Domain Group|Global domain group account for domain administrators||  
|BizTalk Isolated Host Users|Domain Group|Global domain group for accounts with access to the Isolated BizTalk hosts (host processes not running on BizTalk Server, such as HTTP and SOAP).|\<IsolatedSvc\>, \<HostSvc\>|  
|BizTalk Server Administrators|Domain Group|Global domain group account that has the least privileges necessary to perform administrative tasks included in the Configuration Framework Wizard and to administer the BizTalk Server.|\<Admin\>|  
|BizTalk Application Users|Domain Group|Global domain group account for BizTalk application users.|\<HostSvc\>|  
|BizTalk Server Operators|Domain Group|The group that has the least privileges necessary to perform tasks required for operating the BizTalk Server environment after installation.||  
|SharePoint Enabled Hosts|Domain Group|The Windows group that has permissions to call the Windows SharePoint Services Adapter Web services.|\<HostSvc\>|  
|SSO Administrators|Domain Group|Global domain group account for SSO administrators.|\<Admin\>, \<SSOSvc\>|  
|SSO Affiliate Administrators|Domain Group|Global domain group account for SSO affiliate administrators|\<Admin\>|  
|A4SWIFT Users|Domain Group|Global domain group account that has the fewest privileges necessary to perform basic tasks in A4SWIFT.|\<HostSvc\>, Additional Network Users|  
|A4SWIFT Administrators|Domain Group|Global domain group account that has the least privileges necessary to administer A4SWIFT.|\<Admin\>|  
  
> [!NOTE]
>  All group accounts should be global security accounts and not local domain accounts. If local domain group accounts (created using net localgroup) are used, the setup program for [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] cannot validate specific [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] domain users.  
  
## Joining the Domain  
 After you have created the domain and the domain controllers have restarted, join each server to the domain.