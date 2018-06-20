---
title: "How to Start an Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [orchestrations], starting"
  - "starting, orchestrations"
  - "orchestrations, starting"
ms.assetid: 83411279-ee6f-4d68-aa3b-b5cd5e106088
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Start an Orchestration
This topic describes how to use the BizTalk Server Administration console to start an orchestration. When you start an orchestration, it begins processing incoming messages.  
  
 When starting and orchestration, bear in mind the following important points:  
  
-   Before you can start the orchestration, it must be enlisted, along with all of the send ports and send port groups associated with it. For instructions, see [How to Enlist an Orchestration](../core/how-to-enlist-an-orchestration.md) and [How to Enlist a Send Port or Send Port Group](../core/how-to-enlist-a-send-port-or-send-port-group.md).  
  
-   Starting an orchestration does not automatically start any associated send ports. You must start them separately, as described in [How to Start a Send Port or Send Port Group](../core/how-to-start-a-send-port-or-send-port-group.md).  
  
-   If you enlist the send ports and/or send port groups associated with this orchestration, but do not start them, BizTalk Server places any messages sent to this send port or send port group in the suspended queue of the host where you enlisted the send port or send port group.  
  
> [!NOTE]
>  The application developer can start an orchestration to test its functionality during the development process by using the procedure in this topic.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Operators group or the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To start an orchestration  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration that you want to start.  
  
3. Click **Orchestrations**, right-click the orchestration, and then click **Start**.  
  
   > [!IMPORTANT]
   >  If you did not first enlist the associated send port and send port groups before starting the orchestration, you will see an error message.  
  
   > [!NOTE]
   >  To start multiple orchestrations at once, hold down the shift key and select each orchestration, right-click an orchestration, and then click **Start**.  
  
## See Also  
 [Managing Orchestrations](../core/managing-orchestrations.md)   
 [How to Stop an Orchestration](../core/how-to-stop-an-orchestration.md)   
 [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md)