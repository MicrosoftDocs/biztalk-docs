---
title: "Troubleshooting Internet Information Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f77084f1-5797-42ab-bbf6-fe815144232e
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshooting Internet Information Services
Microsoft Internet Information Services (IIS) is used extensively by Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for various functionality including the HTTP, SOAP, and Windows SharePoint Services adapters. This topic describes some known issues that you may encounter with IIS and possible resolutions to these issues.  
  
## Known Issues  
 The errors documented in this topic may not be displayed unless you configure Internet Explorer to disable friendly HTTP error messages.  
  
#### To configure Internet Explorer to disable friendly HTTP error messages  
  
1.  On the **Tools** menu, click **Internet Options**.  
  
2.  On the **Advanced** tab, in the **Browsing** section, clear the **Show friendly HTTP error messages** check box, and then click **OK**.  
  
3.  Close Internet Explorer.  
  
#### "HTTP 404 - File not found" error occurs when accessing a Web page on an IIS server  
  
##### Problem  
 When you attempt to access a Web page on an IIS server an error similar to the following is displayed:  
  
 Page Cannot Be Found  
  
 \- or -  
  
 HTTP 404 - File not found  
  
##### Cause  
 This error may occur for the following reasons:  
  
-   The requested file has been renamed.  
  
-   The requested file has been moved to another location or deleted.  
  
-   The requested file is temporarily unavailable due to maintenance, upgrades, or other unknown causes.  
  
-   The requested file does not exist.  
  
-   IIS 6.0: The appropriate Web service extension or MIME type is not enabled.  
  
-   A virtual directory is mapped to the root of a drive on another server.  
  
##### Resolution  
 Follow the steps in the RESOLUTION section of Microsoft Knowledge Base article 248033, "Common reasons IIS Server returns "HTTP 404 - File not found" error" available at [http://support.microsoft.com/kb/248033](http://support.microsoft.com/kb/248033).  
  
#### "Cannot find server or DNS Error error" occurs when accessing a Web page on an IIS server  
  
##### Problem  
 When you attempt to access a Web page on an IIS server an error similar to the following is displayed:  
  
 The Page Cannot Be Displayed  
  
 \- or -  
  
 Cannot find server or DNS Error  
  
##### Cause  
 This error may occur for the following reasons:  
  
-   Your Internet Explorer connection settings are incorrect.  
  
-   Incorrectly configured, non-functioning, or incompatible firewall or proxy software has been installed.  
  
-   There is an incorrect entry in a Hosts file.  
  
-   Your network adapter is not functioning correctly or you have incompatible network adapter drivers installed.  
  
##### Resolution  
 Follow the steps in the RESOLUTION section of Microsoft Knowledge Base article 326155, "Error message when you try to access a Web site in Internet Explorer: "Page Cannot Be Displayed"" available at [http://support.microsoft.com/kb/326155](http://support.microsoft.com/kb/326155).  
  
#### "401 - Access denied" error occurs when accessing a Web page on an IIS server  
  
##### Problem  
 When you attempt to access a Web page on an IIS server an error similar to the following is displayed:  
  
 401 - Access denied  
  
##### Cause  
 IIS defines several different 401 errors that indicate a more specific cause of the error. These specific error codes are displayed in the browser:  
  
- 401.1 - Logon failed.  
  
- 401.2 - Logon failed due to server configuration.  
  
- 401.3 - Unauthorized due to ACL on resource.  
  
- 401.4 - Authorization failed by filter.  
  
- 401.5 - Authorization failed by ISAPI/CGI application.  
  
- 401.7 – Access denied by URL authorization policy on the Web server. This error code is specific to IIS 6.0.  
  
  For a complete list of the IIS 7.0 status codes, see Microsoft Knowledge Base article 943891, "The HTTP status codes in IIS 7.0" available at [http://support.microsoft.com/kb/943891](http://support.microsoft.com/kb/943891).  
  
##### Resolution  
 Follow the steps in [Guidelines for Resolving IIS Permissions Problems](../core/guidelines-for-resolving-iis-permissions-problems.md) to resolve IIS permissions problems.  
  
#### "500 - Internal server error" occurs when accessing a Web page on an IIS server  
  
##### Problem  
 When you attempt to access a Web page on an IIS server an error similar to the following is displayed:  
  
 500 - Internal server error  
  
##### Cause  
 This error message can be caused by a wide variety of server-side problems.  
  
##### Resolution  
 To resolve the issue, do the following:  
  
- Review the Application log of the IIS server for information about why this error occurs.  
  
- Review the IIS log files or HTTPERR log files for information that may be helpful for determining the cause of the error. By default the IIS log files on a computer running [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] operating systems are located in the following directory:  
  
   <em>%WinDir%\\</em>system32\LogFiles\W3SVC1\  
  
  > [!NOTE]
  >  *%WinDir%* is a placeholder for the location of the Windows directory on the IIS server.  
  
   By default the IIS log files on a computer running Windows Server 2008 or Windows Vista are located in the following directory:  
  
   C:\inetpub\logs\LogFiles\W3SVC1\  
  
   By default the HTTPERR log files on [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] are located in the following directory:  
  
   <em>%WinDir%</em>system32LogFilesHTTPERR  
  
  > [!NOTE]
  >  The HTTPERR log file is only available on a [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], or Windows Vista computer.  
  
#### "Service Unavailable" error occurs when accessing a Web page on an IIS server  
  
##### Problem  
 When you attempt to access a Web page on an IIS server an error similar to the following is displayed:  
  
 Service Unavailable  
  
##### Cause  
 The most common cause for this error is that the application pool (IIS 6.0 and IIS 7.0) for the Web page is stopped. This commonly occurs if the application pool or COM+ application is configured with an Identity for which the specified user name and or password is invalid.  
  
##### Resolution  
 Follow the steps in the "Setting IIS Application Host Process Identity" section of the topic [Guidelines for Resolving IIS Permissions Problems](../core/guidelines-for-resolving-iis-permissions-problems.md) to set the appropriate host process identity.  
  
## See Also  
 [Guidelines for Resolving IIS Permissions Problems](../core/guidelines-for-resolving-iis-permissions-problems.md)