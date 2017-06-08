---
title: "How to Start, Stop, Pause, Resume, or Restart BizTalk Server Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "starting, services"
  - "services, restarting"
  - "services, pausing"
  - "resuming, services"
  - "services, stopping"
  - "services, resuming"
  - "services, starting"
  - "stopping, services"
ms.assetid: 3d6449ba-2892-49c6-a697-847608d10ec5
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Start, Stop, Pause, Resume, or Restart BizTalk Server Services
The following table lists the BizTalk Server services that you can start, stop, pause, resume, or restart:  
  
|Name|Description|Startup Type|Dependencies|  
|----------|-----------------|------------------|------------------|  
|BizTalk Service BizTalk Group: *\<BizTalkServerApplication>*|Provides the BizTalk Server application service.|Automatic|-   Enterprise Single Sign-On (SSO) Service<br />-   Event Log<br />-   Remote Procedure Call (RPC)|  
|Enterprise Single Sign-On Service|Provides single sign-on services to enterprise applications.|Automatic|With SQL Server installed locally:<br /><br /> -   COM+ System Application<br />-   Remote Procedure Call (RPC)<br />-   SQL Server (MSSQLSERVER)<br /><br /> With SQL Server installed remotely:<br /><br /> -   COM+ System Application<br />-   Remote Procedure Call (RPC)None|  
|Rule Engine Update Service|Notifies users about the deployment or undeployment of policies.|Automatic|None|  
  
## Prerequisites  
 To perform this procedure, you must be a member of the Administrators group on the local computer, or you must have been delegated the appropriate authority. If the computer is joined to a domain, members of the Domain Admins group might be able to perform this procedure. As a security best practice, consider using Run as to perform this procedure.  
  
## To start, stop, pause, resume, or restart a BizTalk Server service  
 You can start, stop, pause, resume, or restart a BizTalk Server service by using any of the methods listed below:  
  
-   Using Services in Control Panel  
  
-   Using a command prompt  
  
#### Using Services in Control Panel  
  
1.  Open Services. Click **Start**, click **Run**, and then type **services.msc**.  
  
2.  Right-click the appropriate BizTalk Server service and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.  
  
#### Using a command prompt  
  
1.  Open Command Prompt. Click **Start**, click **Run**, and then type **cmd**.  
  
2.  Type one of the following, where *ServiceName* is the name of the BizTalk Server service you want to start, stop, pause, or resume:  
  
    -   To start a service, type:  
  
         **net start** *ServiceName*  
  
    -   To stop a service, type:  
  
         **net stop** *ServiceName*  
  
    -   To pause a service, type:  
  
         **net pause** *ServiceName*  
  
    -   To resume a service, type:  
  
         **net continue** *ServiceName*  
  
|BizTalk Server Service|ServiceName|  
|----------------------------|-----------------|  
|BizTalk Service BizTalk Group: BizTalkServerApplication|btssvc$biztalkserverapplication|  
|Enterprise Single Sign-On Service|Entsso|  
|Rule Engine Update Service|ruleengineupdateservice|