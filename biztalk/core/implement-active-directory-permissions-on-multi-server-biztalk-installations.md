---
title: "Guidelines for Implementing Active Directory Permissions on Multi Server BizTalk Installations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 315e25c4-b21d-4b5f-a1d2-1e2777b57f9e
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Guidelines for Implementing Active Directory Permissions on Multi Server BizTalk Installations
This topic describes guidelines for creating Active Directory Organizational Units, which consist of the user accounts and groups that you use in a Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation.  
  
 The accounts created herein do not need permissions in the domain beyond those of ordinary users. The domain accounts may need elevated privileges within the trust boundary that includes:  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
- Microsoft [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] (on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] server)  
  
- Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]  
  
- External Database One  
  
- External Database Two  
  
- External Database *N*  
  
  For example, a domain account may need to be granted rights to perform certain actions on the systems hosting external databases. In another case, an account may need to write a file to a file drop folder, requiring write access to the folder.  
  
  Use the **Active Directory Users and Computers** console to create and manage domain user and group accounts. Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Active Directory Users and Computers** to start the **Active Directory Users and Computers** console.  
  
## BizTalk Server Installation and Configuration Account  
 In the development environment, the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation program and the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration Wizard require the use of an account with administrative rights on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] systems. Rights can be revoked or the account disabled as soon as setup and configuration are complete. The account must also belong to several BizTalk groups, covered in the following sections.  
  
> [!NOTE]
>  You will not be able to configure SSO components if the account used for installation belongs to a different Active Directory forest than the server. If you do not have a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installer account, use a local administrator account for SSO configuration. This methodology may create other issues during installation, such as the need to log on to resources using different credentials.  
  
## BizTalk Server Development Accounts  
 Individuals doing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] development require access to adapters, receive and send handlers, and receive locations. This access requires the domain developer group to be members of the **BizTalk Server Administrators** and **SSO Affiliate Administrators** groups.  
  
> [!NOTE]
>  Active Directory has restrictions regarding the types of groups that can contain foreign domain users, and the types of groups that can be contained in other groups. The groups and accounts created below are tested in a multiserver environment on a single domain.  
  
## BizTalk Server Deployment Accounts  
 Individuals deploying [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications will need to be administrators on the local systems and may require other permissions in the environment. A BizTalk Server deployment account is referenced in this topic for this purpose.  
  
 This access requires the domain deployment group to be members of the **BizTalk Server Administrators** and **SSO Affiliate Administrators** groups.  
  
> [!NOTE]
>  You will not be able to configure SSO components if the account used for installation belongs to a different Active Directory forest than the server. If you do not have a BizTalk Server deployment account, use a local administrator account for SSO configuration. This methodology may create other issues during installation, such as the need to log on to resources using different credentials.  
  
## BizTalk Server Support Accounts  
 Individuals supporting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications will need to be administrators on the local systems. A BizTalk support account is referenced in this topic for this purpose.  
  
 This access requires the domain support group to be members of the **BizTalk Server Administrators** group.  
  
## SQL Server Service Accounts  
 The service running the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance must belong to the same Active Directory domain as the accounts installing, developing, and deploying [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] components.  
  
- Use **SQLAdmin** for administrative functions (interactive logon).  
  
- Use **SQLService** to manage the service (no interactive logon).  
  
- Use **SQLAccess** to access external databases.  
  
- SQLAdmin must be a member of the local Administrators group on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] system.  
  
- SQLService must be a member of the local Administrators group on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] system and needs to be granted the **Log on as a service** user right.  
  
- SQLAccess needs appropriate rights on the remote database servers.  
  
  **SQL Accounts:**  
  
|**User name**|**First Name**|**Last Name**|**Full Name**|  
|-------------------|--------------------|-------------------|-------------------|  
|SQLService|SQL|SQLService|SQL Service Account|  
|SQLAdmin|Admin|SQLService|SQL Admin Account|  
|SQLAccess|Access|SQLService|SQL Access Account|  
  
 Set account passwords according to company standards.  
  
> [!IMPORTANT]
>  On the computer running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], modify the startup parameters for the SQL Server and SQLServerAgent services to use the SQLService account and credentials.  
> 
> [!NOTE]
>  The Username fields are samples; you may need to change the names to avoid conflicting with other Active Directory accounts.  
  
## Windows SharePoint Services Account  
 The Windows SharePoint Services accounts must be created prior to installing [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].  
  
 Recommendations and notes on the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] account:  
  
- Use the SharePoint Admin Account (SPAdmin) for administrative functions, SharePoint Timer Service and all [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] access.  
  
- SPAdmin is the site owner and will need an e-mail alias.  
  
- SPAdmin must be a member of the local administrators group on the local [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer (Windows SharePoint Services setup does this).  
  
- SPAdmin must have the security administrator and database creator roles on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer (Windows SharePoint Services setup does this).  
  
  **Sharepoint Accounts:**  
  
|**User name**|**First Name**|**Last Name**|**Full Name**|  
|-------------------|--------------------|-------------------|-------------------|  
|SPAdmin|Admin|SPService|SharePoint Admin Account|  
  
 Set account passwords according to company standards and be able to retrieve these passwords during the configuration steps. Refer to the **Passwords** section of this topic for issues surrounding generated passwords.  
  
> [!NOTE]
>  This Username field is a sample; you may need to change this name to protect other AD accounts.  
> 
> [!IMPORTANT]
>  After installing Windows SharePoint Services on the computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], confirm that the startup parameters for the SharePoint Timer Service is using the SPAdmin account and credentials.  
  
## BizTalk Groups and Users  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Groups and Users must be created prior to running the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration Wizard. In a single-system installation, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses local groups and accounts which are created during configuration. However, if separate [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hosts are deployed or if [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] are installed on two different computers you must use domain user and group accounts.  
  
> [!NOTE]
>  The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration Wizard cannot create domain accounts.  
  
 Recommendations and notes on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] service and user accounts:  
  
- Create an Organizational Unit (OU) for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. All accounts and groups will belong to this OU.  
  
- Be descriptive with full names; the names in the following lists should enable the installer to select the proper groups/accounts/users during configuration.  
  
- First name and last name are optional; included for consistency only.  
  
- The differentiator **BTService** and **BTUser** refers to service accounts (automatons) and generic/shared human users.  
  
- Create domain accounts and populate them via an ADSI script for user and group account creation for up line environments.  
  
  **BizTalk Service Accounts**  
  
|**User name**|**First Name**|**Last Name**|**Full Name**|  
|-------------------|--------------------|-------------------|-------------------|  
|BTService|BTS|BTService|BizTalk Service Account|  
|BTServiceHost|Host|BTService|BizTalk Host Instance Account|  
|BTServiceHostIso|HostIso|BTService|BizTalk Isolated Host Instance Account|  
|SSOService|SSO|BTService|Enterprise Single Sign-On Service|  
|BTServiceREU|REU|BTService|Rule Engine Update Service|  
  
 Set user names according to company and environmental standards (for example, devBTService, alphaBTService). Set account passwords according to company standards and be able to retrieve them for the configuration steps. Refer to the **Password Considerations for Development** section of this topic for issues surrounding generated passwords.  
  
 The installer will notice the service accounts are quite granular, with a near one-to-one mapping to the services created by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. The granularity allows corporate IT security to track or restrict access as needed. The granularity is recommended, but it is up to the system designer and enterprise security personnel to determine if it is necessary in the enterprise environment.  
  
 The service accounts in the previous group are intended for automaton access only, not for interactive logon by users.  
  
#### To set the appropriate account options  
  
1. In the **Active Directory Users and Computers** console, click to expand the domain, and then click to expand the **Users** container.  
  
2. Right-click the account and then select **Properties** to display the **Properties** dialog box for the account.  
  
3. Click the **Account** tab of the **Properties** dialog box.  
  
4. Click to check the following options:  
  
   -   **User cannot change password** (enterprise security will batch change the passwords).  
  
   -   **Password never expires**  
  
5. Click the **Log On To** button to display the **Logon Workstations** dialog box.  
  
6. Click the option for **The following computers**, add each computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], and then click **OK**.  
  
7. Click the **Remote Control** tab of the **Properties** dialog box, and then click to clear the option to **Enable remote control**.  
  
8. Click the **Terminal Services Profile** tab of the **Properties** dialog box.  
  
9. Click to check the option to **Deny this user permissions to log on to any Terminal Server**.  
  
10. Click **OK** to close the **Properties** dialog box for the account.  
  
11. Repeat steps 3 through 10 for each service account.  
  
    **BizTalk User Accounts**  
  
|**User name**|**First Name**|**Last Name**|**Full Name**|  
|-------------------|--------------------|-------------------|-------------------|  
|BTUserAdmin|Admin|BTUser|BizTalk Administrative User Account|  
|BTUserDeploy|Deploy|BTUser|BizTalk Deployment User Account|  
|BTUserHostInstance|HostInstance|BTUser|BizTalk Host Instance Account|  
|BTUserHostIsolated|IsolatedlHost|BTUser|BizTalk Isolated Host Instance Account|  
|BTUserInstall|Install|BTUser|BizTalk Installation User Account|  
|BTUserSupport|Support|BTUser|BizTalk Support Access Account|  
  
#### To set the appropriate account options follow these steps  
  
1. In the **Active Directory Users and Computers** console click to expand the domain, and then click to expand the **Users** container.  
  
2. Right-click the account and then select **Properties** to display the **Properties** dialog box for the account.  
  
3. Click the **Account** tab of the **Properties** dialog box.  
  
4. Click to check the following options:  
  
   -   **User cannot change password** (enterprise security will batch change the passwords).  
  
   -   **Password never expires**  
  
5. Click the **Log On To** button to display the **Logon Workstations** dialog box.  
  
6. Click the option for **The following computers**, add each computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], and then click **OK**.  
  
7. Click the **Remote Control** tab of the **Properties** dialog box, and then click to check the option to **Enable remote control**.  
  
8. Click the **Terminal Services Profile** tab of the **Properties** dialog box.  
  
9. Click to clear the option to **Deny this user permissions to log on to any Terminal Server**.  
  
10. Click **OK** to close the **Properties** dialog box for the account.  
  
11. Repeat steps 3 through 10 for each user account.  
  
    > [!NOTE]
    >  Any of these accounts can be disabled if the roles they are to provide are assigned to actual users. In the early stages of release one and release two, it is assumed that these accounts are used in the development, alpha test, and beta test environments.  
  
    **BizTalk Group Accounts**  
  
|**Group Name**|**Group Type**|**Members**|  
|--------------------|--------------------|-----------------|  
|BizTalk Application Users|Global or Universal|-   BTServiceHost<br />-   BTUserHostInstance|  
|BizTalk Development Users|Global or Universal|(local domain accounts of development users) **Note:**  As a best practice, do not enable the BizTalk Development Users group in up-line environments.|  
|BizTalk Deployment Users|Global or Universal|(local domain accounts of deployment users)|  
|BizTalk Host Users|Global or Universal|BTUserHostInstance|  
|BizTalk Isolated Host Users|Global or Universal|-   BTServiceHostIso<br />-   BTUserHostInstance|  
|BizTalk Server Administrators|Global or Universal|-   BTUserAdmin<br />-   BTUserInstall<br />-   BizTalk Development Users<br />-   BizTalk Deployment Users|  
|BizTalk Support Users|Global or Universal|BTUserSupport (local domain accounts of support users)|  
|SSO Administrators|Global or Universal|-   SSOService<br />-   BTUserInstall<br />-   Local Administrator|  
|SSO Affiliate Administrators|Global or Universal|-   BizTalk Development Users<br />-   BizTalk Deployment Users<br />-   BTServiceHostIso<br />-   \<console user\>|  
|Windows SharePoint Services Administrators|Global or Universal|-   SPAdmin<br />-   BTUserInstall<br />-   BTUserDeploy<br />-   BizTalk Development Users<br />-   BizTalk Deployment users|  
  
 Recommendations and notes on domain groups:  
  
- Create the groups and add members prior to installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
- Domain groups can be Global or Universal groups.  
  
- Use *\<DomainName\>\\<UserName\>* when specifying domain account information in the Configuration Wizard.  
  
- Groups and user/service accounts must belong to the domain in which the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer belongs (the Configuration Wizard checks this and will not display accounts or groups containing accounts from other domains).  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] requires domain accounts for all clustering scenarios.  
  
- When installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the console user needs to be a member of the following groups:  
  
  - BizTalk Server Administrators  
  
  - SSO Administrators (only when configuring the master secret server)  
  
  - Windows administrator  
  
  - [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] administrator  
  
  - OLAP administrator  
  
    The BTUserInstall account should be used for installation and configuration and should be disabled after configuration is complete.  
  
- To allow message event and service instance tracking to attach orchestrations to the debugger, the developer needs to belong to the BizTalk Server Administrators group, as outlined above in the section **BizTalk Development Accounts**.  
  
## Local Administrator Accounts  
 Confirm or add the following accounts and groups to the Local Administrators group on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer:  
  
- Domain\BTUserInstall (disable when configuration is complete)  
  
- Domain\BTUserDeploy (disable in production when deployment is complete)  
  
- Domain\SPAdmin  
  
- Domain\SQLAdmin  
  
- Domain\SQLService  
  
- Domain\BizTalk Development Users (omit in up line environments)  
  
- Domain\BizTalk Deployment Users (omit in development environments)  
  
  Confirm or add the following accounts and groups to the Local Administrators group on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer:  
  
- Domain\BTUserInstall (disable when configuration is complete)  
  
- Domain\BTUserDeploy (disable in production when deployment is complete)  
  
- Domain\BTUserSupport  
  
- Domain\SPAdmin  
  
- Domain\BizTalk Development Users (omit in upline environments)  
  
- Domain\BizTalk Deployment Users (omit in development environments)  
  
## SQL Server Administrator Accounts  
 Setup programs accept input from the installer and assigns SQL roles to users and groups:  
  
- During [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] setup, the SPAdmin account is granted Security Administrator and Database Creator rights on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer. These rights can be removed if the SPAdmin account is a member of the Local Administrators group.  
  
## E-Mail Account  
 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] will send mail based on certain system events. Setup prompts for an e-mail address during the configuration process. Create e-mail aliases for this purpose and monitor the alias during setup and unit testing. In the production environment, this account should be accessible by a system administrator who is monitoring the system.  
  
 The e-mail account used by [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] is the **WSS Administrator E-mail** account.  
  
## Password Considerations for Development  
 For development and test environments, account passwords can be set by a standard and be distributable. Installer standards vary; this topic uses the template of initial capital letters abbreviating the service component followed by a lower-case abbreviation for the rest of the account (service or user). For service accounts, this topic uses 'Serv', for user accounts this topic uses 'User'.  
  
 For example:  
  
- Windows SharePoint Services (SharePoint) Service and admin account (SPAdmin) passwords: 'SPServ'.  
  
- BizTalk Service account passwords: 'BTServ'.  
  
- BizTalk User account passwords: 'BTUser'.  
  
  Some IT environments require passwords to contain non-alpha and/or numeric characters. In this scenario you could substitute a dollar sign ($) for "s", and an 'at' sign (@) for "a". The symbols are samples; develop a pattern that works best for you for shared accounts with semi-public passwords.  
  
  Sample redistributable passwords in use in the development environment are:  
  
- BT$erv99           BizTalk Service Accounts  
  
- BTU$er99          BizTalk User Accounts  
  
- SP$erv99           WSS Service Account (SPAdmin)  
  
- SQL$erv99         SQL Service/Access/Admin Account  
  
> [!NOTE]
>  These recommendations are for development and shared environments only and do not recommend or discourage the use of corporate password policies. See your network administrator for password requirements.  
  
> [!NOTE]
>  If corporate password policy includes generated passwords, be advised that some symbols and symbol combinations are special-use characters to XML. Inappropriate use of these characters will prevent configuration XML files from being opened during the configuration process. These symbols include "&", "\<", "\>", single- and double-quote, and may include others. Test the configuration XML file prior to executing file-based configuration. You can test this reliably for proper XML formatting by opening the document in Internet Explorer (or an XML editor) with the generated passwords embedded therein.  
  
 For more information about deployment of secure passwords in up-line environments (including the method to test a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration file), see [Configuration Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/aa58c43f-8f0e-4a5c-89b9-db7b8a852a72).  
  
## See Also  
 [Troubleshooting BizTalk Server Permissions](../core/troubleshooting-biztalk-server-permissions.md)