---
title: "Steps to restart the services, or shut down | Microsoft Docs"
description: Start, Stop, Pause, Resume, or Restart BizTalk Server services, or shut down the BizTalk Server computer
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d6449ba-2892-49c6-a697-847608d10ec5
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Restart BizTalk services, or shut down the BizTalk Server

The following table lists the BizTalk Server services that you can start, stop, pause, resume, or restart:  
  
|Name|Description|Startup Type|Dependencies|  
|----------|-----------------|------------------|------------------|  
|BizTalk Service BizTalk Group: *\<BizTalkServerApplication\>*|Provides the BizTalk Server application service.|Automatic|-   Enterprise Single Sign-On (SSO) Service<br />-   Event Log<br />-   Remote Procedure Call (RPC)|  
|Enterprise Single Sign-On Service|Provides single sign-on services to enterprise applications.|Automatic|With SQL Server installed locally:<br /><br /> -   COM+ System Application<br />-   Remote Procedure Call (RPC)<br />-   SQL Server (MSSQLSERVER)<br /><br /> With SQL Server installed remotely:<br /><br /> -   COM+ System Application<br />-   Remote Procedure Call (RPC)None|  
|Rule Engine Update Service|Notifies users about the deployment or undeployment of policies.|Automatic|None|  
  
 
## Start, stop, pause, resume, or restart a BizTalk Server service  
 You can start, stop, pause, resume, or restart a BizTalk Server service by using Services.msc, or using the command prompt.

### Prerequisites  
 To perform this procedure, you must be a member of the Administrators group on the local computer, or you must have been delegated the appropriate authority. If the computer is joined to a domain, members of the Domain Admins group might be able to perform this procedure. As a security best practice, consider using Run as to perform this procedure. 
  
### Use Services in Control Panel  
  
1.  Open Services. Click **Start**, click **Run**, and then type **services.msc**.  
  
2.  Right-click the appropriate BizTalk Server service and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.  
  
### Use a command prompt  
  
1.  From the start menu, right-click **Command prompt**, select **More**, and select **Run as Administrator**
  
2.  Type one of the following, where *ServiceName* is the name of the BizTalk Server service you want to start, stop, pause, or resume:  
  
    -   To start a service, type:  
  
         **net start** *ServiceName*  
  
    -   To stop a service, type:  
  
         **net stop** *ServiceName*  
  
    -   To pause a service, type:  
  
         **net pause** *ServiceName*  
  
    -   To resume a service, type:  
  
         **net continue** *ServiceName*  

    |BizTalk service|ServiceName|  
    |---|---|  
    |BizTalk Service BizTalk Group: BizTalkServerApplication|btssvc$biztalkserverapplication|  
    |Enterprise Single Sign-On Service|Entsso|  
    |Rule Engine Update Service|ruleengineupdateservice|
  
## Shut down BizTalk Server  

### Prerequisites  
-   Sign in with an account that is a member of the local administrators group on the BizTalk server that you want to shut down. This is necessary so you can stop services.  
-   Sign in with an account that is a member of the BizTalk Server Administrators group or BizTalk Server Operators group. 

### Task overview
1. Disable receive locations, and stop orchestrations and send ports by performing a partial stop on every active application. You should perform a full stop only if you intend to remove or redeploy an application. For more information, see [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).  
  
2. Stop host instances. For more information, see [How to Stop a Host Instance](../core/how-to-stop-a-host-instance.md).  
  
3. Shut down [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services. See **How to Start, Stop, Pause, Resume, or Restart BizTalk Server Services** (in this topic).
  
4. Shut down Internet Information Services (IIS), or stop [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application pools and Web sites. If you are going to shut down the server entirely you can skip this step. If you are stopping [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for maintenance or to deploy or undeploy a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application, you should perform this step. When you stop only the Web sites and application pools associated with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], other IIS-related processes will continue to run.  
  
    How you proceed with this step depends to some extent on which version of IIS you are using. IIS 6 permits you to stop application pools and Web sites. With IIS 6 you can also stop the IIS Admin Service to shut down all IIS activity including application pools and Web sites. IIS 7.0 is more modular than IIS 6.0, and there is no single switch you can use to stop all IIS 7.0 activities, so you will need to stop Web sites and application pools separately.  
  
    For a list of application pools and virtual applications (Web sites and Web services) used by BizTalk Server, see [Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md).  
  
   For information about starting and stopping application pools in IIS, see [http://go.microsoft.com/fwlink/?LinkID=140513](http://go.microsoft.com/fwlink/?LinkID=140513).  
  
   For information about starting and stopping the Web Server in IIS, see [http://go.microsoft.com/fwlink/?LinkId=140695](http://go.microsoft.com/fwlink/?LinkId=140695).  
  
## See Also  
 [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md)   
 [How to Stop a Host Instance](../core/how-to-stop-a-host-instance.md)   