---
title: "Guidelines for Resolving IIS Permissions Problems | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "troubleshooting"
ms.assetid: d9793a90-3aa3-46ab-a317-6d1e0fbfc1ef
caps.latest.revision: 30
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Guidelines for Resolving IIS Permissions Problems
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] makes extensive use of Microsoft Internet Information Services (IIS) for Web services support and for use with the HTTP, SOAP, and Windows SharePoint Services adapters.  
  
 It is helpful to understand how IIS implements application isolation before troubleshooting IIS permissions problems.  
  
 IIS provides functionality for creating IIS applications as distinct host processes that are run in their own memory space. Once you create an IIS application host, then you must define two sets of permissions, the IIS application host **process identity** and the IIS application host **user access rights**. You should examine each of these permissions sets when troubleshooting IIS permissions problems.  
  
> [!NOTE]
>  The **process identity** and **user access rights** are also referred to as the **security context** of the IIS application host process.  
  
 This topic describes how to set **process identity** and **user access rights** for an IIS application host process and gives some general guidelines for resolving IIS permissions problems.  
  
## Setting IIS Application Host Process Identity  
 Configuration of an IIS application host process can vary depending on the level of functionality being served by the host process. For example, an IIS application host process that only serves static HTML pages is typically configured differently than an IIS application host process that serves ASP pages or ASP.NET applications.  
  
 Configuration of an IIS application host process also varies depending on the version of IIS that is hosting the application. The host process identity of applications running on Windows Server 2008 (IIS 7.0) is governed by the identity of the application pool associated with the application.  
  
### Setting IIS Process Identity for IIS 7.0 on Windows Server 2008 or Windows Vista  
  
1.  Click **Start**, then **All Programs**, and click **Internet Information Services (IIS) 7 Manager**.  
  
2.  In Internet Information Services (IIS) Manager, expand *\<computer name>***(User account)** and click **Application Pools**.  
  
3.  Right-click an application pool and click **View Applications** to see the applications associated with the application pool.  
  
4.  Right-click an application pool and click **Advanced Settings** to display the Advanced Settings dialog for the application pool.  
  
5.  Modify the identity for the application pool by clicking the ellipsis (…) button next to **Identity** under the **Process Model** section of the **Advanced Settings** dialog box.  
  
## Setting User Access Rights for the IIS Server  
 While process identity governs the security context available to the running IIS application host process, user access permissions govern the security context for the account that is actually accessing the Web page(s) being served. Permissions must be set appropriately for both security contexts to avoid permissions errors.  
  
 IIS 7.0 supports the following user authentication methods:  
  
-   **Anonymous access:** Allows users to establish an anonymous connection. The IIS server logs on the user with the specified guest account.  
  
-   **ASP.NET Impersonation** Allows an application to run in one of two different contexts: either as the user authenticated by IIS or as an arbitrary account that you set up.  
  
-   **Basic authentication:** Transmits passwords across the network in plaintext, an unencrypted form.  
  
-   **Digest authentication:** Works only with Active Directory accounts, sending a hash value over the network, rather than a plaintext password. Digest authentication works across proxy servers and other firewalls and is available on Web Distributed Authoring and Versioning (WebDAV) directories. Use of Digest authentication requires that Anonymous authentication is disabled first.  
  
-   **Forms Authentication** Accommodates authentication for high-traffic sites or applications on public servers. Forms authentication lets you manage client registration and authentication at the application level, instead of relying on the authentication mechanisms provided by the operating system.  
  
-   **Windows authentication:** Uses authentication on your Windows domain to authenticate client connections.  
  
#### To set user access rights for a virtual directory in IIS 7.0  
  
1.  In the Internet Information Services (IIS) Manager, expand *\<computer name>*, **Sites**, and **Default Web Site** in the **Connections** pane.  
  
2.  Click to select the virtual directory and click the **Features View** at the bottom of the Workspace pane to list the configurable features for the virtual directory.  
  
3.  Double-click the **Authentication** feature in the Workspace pane to list the authentication methods that are enabled for the virtual directory.  
  
4.  Click to select the authentication method that you would like to enable or disable and click either **Disable** or **Enable** in the **Actions** pane of the IIS Manager.  
  
    > [!NOTE]
    >  If **Enable anonymous access** is enabled, IIS will set user access rights as the configured Anonymous user identity before setting user access rights with any other enabled authentication methods.  
    >   
    >  To configure the Anonymous user identity, right-click the **Anonymous Authentication** method and click **Edit** to display the **Edit Anonymous Authentication Credentials** dialog.  
  
## General Guidelines for Resolving IIS Permissions Problems  
 Follow these steps to troubleshoot IIS permissions:  
  
1.  Check the application log of the IIS Server computer for errors.  
  
2.  Follow the steps in [IIS 7.0: Configuring Tracing for Failed Requests in IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=130600) to troubleshoot permissions problems on IIS 7.0 computers.  
  
3.  Check the IIS log files of the IIS server for HTTP 401 errors.  
  
     By default the IIS log files on a computer running Windows Server 2008 or Windows Vista are located in the following directory:  
  
     C:\inetpub\logs\LogFiles\W3SVC1\  
  
    -   If the IIS log file for an IIS 7.0 computer contains HTTP 401 errors, follow the steps in Microsoft Knowledge Base article 943891, "The HTTP status codes in IIS 7.0" available at [http://support.microsoft.com/kb/943891](http://support.microsoft.com/kb/943891) to determine the substatus code and to troubleshoot the permissions problem based on the status code.  
  
    -   Check the value of the **cs-username** field associated with the HTTP 401 error. This field contains the name of the authenticated user who accessed the IIS server. The anonymous user account is represented by a hyphen (-) in this field. Ensure that this account has permissions on the appropriate resources.  
  
4.  Verify that the process identity credentials used by the IIS application host process are set correctly and that the account has the appropriate permissions. If the account used for the process identity has insufficient permissions then either change the account or grant the account the appropriate permissions.  
  
5.  Use the RegMon and FileMon utilities described in [Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md) to diagnose file or registry access permissions problems.  
  
## See Also  
 [Troubleshooting BizTalk Server Permissions](../core/troubleshooting-biztalk-server-permissions.md)   
 [IIS 7.0: Configuring Authentication in IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=129909)