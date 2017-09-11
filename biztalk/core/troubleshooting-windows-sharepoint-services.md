---
title: "Troubleshooting Windows SharePoint Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9acf9a0d-2c92-4227-80f8-b2d0cca0c232
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshooting Windows SharePoint Services
Microsoft [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] is used by the Windows SharePoint Services adapter. This topic describes some known issues that may be encountered with Windows SharePoint Services and possible resolutions to these issues.  
  
## Known Issues  
  
#### Login failed for user 'NT AUTHORITY\NETWORK SERVICE' error occurs when attempting to create content database  
  
##### Problem  
 When you attempt to create a content database using the SharePoint Central Administration Web site, an error similar to the following is displayed:  
  
 Login failed for user 'NT AUTHORITY\NETWORK SERVICE'  
  
##### Cause  
 This issue occurs when the database owner of the database that you are connecting to is different from the application pool identity that Windows SharePoint Services is running under.  
  
##### Resolution  
 To resolve this issue, do one of the following:  
  
-   Grant the NETWORK SERVICE account "Database Creation" rights in SQL Server.  
  
-   Change the application pool identity account to an account that has "Database Creation" rights in SQL Server.  
  
#### "Service Unavailable" error occurs when accessing the SharePoint Central Administration Web site  
  
##### Problem  
 When you attempt to open the SharePoint Central Administration Web site, an error similar to the following is displayed:  
  
 Service Unavailable  
  
##### Cause  
 The most common cause for this error is that the application pool (IIS 6.0 or IIS 7.0) or hosting COM+ application (IIS 5.x) for the SharePoint Central Administration Web site is stopped. This commonly occurs if the application pool or COM+ application is configured with an identity for which the specified user name and/or password is invalid.  
  
##### Resolution  
 Follow the steps in the "Setting IIS Application Host Process Identity" section of the topic [Guidelines for Resolving IIS Permissions Problems](../core/guidelines-for-resolving-iis-permissions-problems.md) to set the appropriate host process identity.  
  
#### "Cannot connect to the configuration database" error occurs when attempting to extend and create a content database  
  
##### Problem  
 When you attempt to extend and create a content database using the SharePoint Central Administration Web site, an error similar to the following is displayed:  
  
 Cannot connect to the configuration database  
  
##### Cause  
 This issue occurs when the account that is used by the application pool that is running the SharePoint Central Administration Web site does not have the required permissions to the SQL Server database.  
  
##### Resolution  
 To resolve this issue, do one of the following:  
  
-   Grant the account that is used by the application pool for the SharePoint Central Administration Web site "Database Creation" rights in SQL Server.  
  
-   Change the application pool identity account to an account that has "Database Creation" rights in SQL Server.  
  
#### "The SharePoint Timer Service service failed to start" error is generated in the Application log after rebooting server  
  
##### Problem  
 After restarting the server, you see the following error in the event logs:  
  
 The SharePoint Timer Service service failed to start  
  
 You may also see the following error when you open the SharePoint Central Administration site:  
  
 Unable to connect to the WSS configuration database STS_Config  
  
##### Cause  
 This error occurs when the SharePoint Timer service fails to contact the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] database after rebooting. The SharePoint Timer service is used to send notifications and perform scheduled tasks for [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]. The most common reason that the SharePoint Timer service fails to start is that the account used to run the service is configured with an identity for which the user name and/or password are no longer valid.  
  
##### Resolution  
 Ensure that the user name and password specified for the SharePoint Timer service logon account are correct and that the service has been started.  
  
## See Also  
 [How to configure a Windows SharePoint Services virtual server](http://support.microsoft.com/kb/832769)   
 [How to back up and restore installations of Windows SharePoint Services that use Microsoft SQL Server 2000 Desktop Engine (Windows)](http://support.microsoft.com/kb/833797)   
 [You receive a "Cannot connect to the configuration database" error message when you connect to your Windows SharePoint Services Web site](http://support.microsoft.com/kb/823287)   
 [You Receive a "Service Unavailable" Error Message When You Browse a Windows SharePoint Services Web Site](http://support.microsoft.com/kb/823552)   
 [You receive a "Database <Database_Name> already exists" error message when you manage your Windows SharePoint Services content database](http://support.microsoft.com/kb/828815)