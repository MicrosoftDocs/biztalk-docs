---
title: "Application Deployment and Management Tools | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: de85b52b-7eb7-4cf1-b8b4-41f7488b4d2f
caps.latest.revision: 29
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Application Deployment and Management Tools

## Overview
This topic briefly describes the tools that you can use for deploying and managing a BizTalk application and then summarizes the operations you can perform with each tool. A table at the end of this topic summarizes the tasks you can perform using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console and BTSTask.  

- **BizTalk Server Administration console.** The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, a Microsoft Management Console (MMC), is the primary management tool for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. It provides a graphical user interface for performing all of the deployment and management operations for a BizTalk application. For example, from the administration console, you can start the Import, Installation, and Export Wizards as well as add and remove an application's artifacts and make other modifications to the application.  

   You also generate BizTalk .msi files for your BizTalk applications by using either the Export MSI File Wizard or BTSTask, described next. You can then install the application on a computer from the .msi file or import the application from the .msi file into another BizTalk group. For more information about the administration console, see [Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md).  

- **BTSTask command-line tool.** BTSTask allows you to perform many application management tasks from the command line. For more information about using BTSTask, see [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md).  

- **Scripting and programmability APIs**. You can use Microsoft Windows Management Instrumentation (WMI) to create and run scripts that automate many application management tasks. For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  

- **Visual Studio.** The developer can create BizTalk assemblies in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and use the Deploy command to automatically deploy them into a BizTalk application. For more information, see [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).  

   .  

  > [!IMPORTANT]
  >  You should never deploy an assembly from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] running on a production computer. This can disrupt running applications. For more information, see [Best Practices for Deploying a BizTalk Application](../core/best-practices-for-deploying-a-biztalk-application.md).  

## Tool by the task  
 The following table summarizes the tasks you can perform by using the administration console and BTSTask.  


|                                        Task                                         |                                                                                       Tool                                                                                       |
|-------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                           Export an application .msi file                           |           -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console <br/>– Export MSI File Wizard<br />-   BTSTask           |
|                           Import an application .msi file                           |             -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console <br/>– Import MSI Wizard<br />-   BTSTask              |
|                           Create or delete an application                           |                          -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console<br />-   BTSTask                          |
|                               Install an application                                | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console <br/>– Installation Wizard (or double-click the application .msi file) |
|                              Uninstall an application                               |                                                              BTSTask (or use Add or Remove Programs Control Panel)                                                               |
|       Add artifacts to an application or remove artifacts from an application       |                          -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console<br />-   BTSTask                          |
|                    Import and export bindings and binding files                     |                          -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console<br />-   BTSTask                          |
|                             Import and export policies                              |                          -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console<br />-   BTSTask                          |
|                            Start and stop an application                            |                                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console                                     |
| Change the state of an artifact: start, stop, enable, disable, enlist, and unenlist |                                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console                                     |
|                              Edit artifact properties                               |                                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console                                     |
|       Create a send port, send port group, receive location, or receive port        |                                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console                                     |

## See Also  
[Administrative and performance tools](../core/administration-tools.md)  
 [Understanding BizTalk Application Deployment and Management](../core/understanding-biztalk-application-deployment-and-management.md)