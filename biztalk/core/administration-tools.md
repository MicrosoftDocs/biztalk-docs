---
title: "Administration Tools | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.ops.admintools"
helpviewer_keywords: 
  - "BAM Event Bus Service"
  - "Scripting and programmability APIs"
  - "BizTalk Explorer"
  - "BAM"
  - "BAM Management utility"
  - "configuration schema [BAM]"
  - "HAT"
  - "tools, about BizTalk Server tools"
  - "BTSTask command-line tool"
  - "administration tools"
  - "BAM Query Web service"
  - "BTSdeploy command-line tool"
  - "tools"
  - "Administration Console [BizTalk Server]"
ms.assetid: 932814f7-2ab3-45cb-8bbc-eaf00fcb24a0
caps.latest.revision: 28
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Administration Tools
You can use the following tools to administer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], to manage [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groups, to deploy [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications, to interact with trading partners, and to monitor the status of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:  
  
-   **BizTalk Server Administration console**. The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console is the primary management tool for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. It provides a graphical user interface for performing all of the deployment operations for a BizTalk application. For example, you can start the Import, Installation, and Export Wizards as well as add and remove an application's artifacts and make other modifications to the application.  
  
     Using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, you can use view live or archived message event or service instance data to track the health of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] implementation, identify bottlenecks, and monitor the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment. You can view the technical details of a particular orchestration, pipeline, or message instance, as well as see the message flow of a particular message that enters the system.  
  
     For information about using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, see [Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md).  
  
-   **BTSTask command-line tool**. BTSTask enables you to perform many administrative tasks from the command line. For more information about using BTSTask, see [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md).  
  
-   **Scripting and programmability APIs**. You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks. For information about using WMI, see [WMI Class Reference](../core/wmi-class-reference.md)  
  
     The WMI object model exposes and simplifies administrative APIs. All administration APIs expose some form of the following operations on every object they manage: create, enumerate, modify, and delete. WMI exposes this functionality in a consistent manner for all WMI objects.  
  
-   **Business Activity Monitoring (BAM).** BAM uses a Microsoft [!INCLUDE[btsOfficeNoVersion](../includes/btsofficenoversion-md.md)][!INCLUDE[btsExcel](../includes/btsexcel-md.md)] workbook to provide business users with a way to see a real-time holistic view of business processes. For more information about BAM, see [Using Business Activity Monitoring](../core/using-business-activity-monitoring.md).  
  
## See Also  
 [Application Deployment and Management Tools](../core/application-deployment-and-management-tools.md)