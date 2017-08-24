---
title: "How to Shut Down BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1aaa815e-281a-4696-9c71-498530186ce5
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Shut Down BizTalk Server
This topic describes how to perform an orderly shutdown of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for maintenance. You can also use this procedure to deploy or undeploy a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application. Following this procedure will help to avoid orphaned messages.  
  
## Prerequisites  
  
-   You must be logged on with an account that is a member of the local administrators group on the BizTalk server that you want to shut down. This is necessary so you can stop services.  
  
-   You must be logged on with an account that is a member of the BizTalk Server Administrators group or BizTalk Server Operators group.  
  
## To shut down BizTalk Server  
  
1.  Disable receive locations, and stop orchestrations and send ports by performing a partial stop on every active application. You should perform a full stop only if you intend to remove or redeploy an application. For more information, see [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).  
  
2.  Stop host instances. For more information, see [How to Stop a Host Instance](../core/how-to-stop-a-host-instance.md).  
  
3.  Shut down [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services. For more information, see [How to Start, Stop, Pause, Resume, or Restart BizTalk Server Services](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).  
  
4.  Shut down Internet Information Services (IIS), or stop [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application pools and Web sites. If you are going to shut down the server entirely you can skip this step. If you are stopping [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for maintenance or to deploy or undeploy a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application, you should perform this step. When you stop only the Web sites and application pools associated with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], other IIS-related processes will continue to run.  
  
     How you proceed with this step depends to some extent on which version of IIS you are using. IIS 6 permits you to stop application pools and Web sites. With IIS 6 you can also stop the IIS Admin Service to shut down all IIS activity including application pools and Web sites. IIS 7.0 is more modular than IIS 6.0, and there is no single switch you can use to stop all IIS 7.0 activities, so you will need to stop Web sites and application pools separately.  
  
     For a list of application pools and virtual applications (Web sites and Web services) used by BizTalk Server, see [Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md).  
  
 For information about starting and stopping application pools in IIS 7.0, see [http://go.microsoft.com/fwlink/?LinkID=140513](http://go.microsoft.com/fwlink/?LinkID=140513).  
  
 For information about starting and stopping the Web Server in IIS 7.0, see [http://go.microsoft.com/fwlink/?LinkId=140695](http://go.microsoft.com/fwlink/?LinkId=140695).  
  
## See Also  
 [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md)   
 [How to Stop a Host Instance](../core/how-to-stop-a-host-instance.md)   
 [How to Start, Stop, Pause, Resume, or Restart BizTalk Server Services](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md)   