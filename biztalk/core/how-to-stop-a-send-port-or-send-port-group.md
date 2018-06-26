---
title: "How to Stop a Send Port or Send Port Group | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [send ports], stopping"
  - "managing [send port groups], stopping"
  - "stopping, send ports"
  - "send port groups, stopping"
  - "stopping, send port groups"
  - "send ports, stopping"
ms.assetid: a7a5eab3-34fe-4417-900a-c37ec16ec009
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Stop a Send Port or Send Port Group
This topic describes how to use the BizTalk Server Administration console to stop a send port or send port group. When you stop a send port or send port group, it no longer processes messages. BizTalk Server suspends all activation messages to a stopped send port or send port group. Stopping a send port group does not affect the state of any send ports that it contains.  
  
> [!NOTE]
>  By default, starting a BizTalk application starts all of the artifacts that it contains. For more information, see [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Operators group or the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To stop a send port or send port group  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the send port or send port group that you want to stop.  
  
3. Click **Send Ports** or **Send Port Groups**, right-click the send port or send port, and then click **Stop**.  
  
## See Also  
 [Managing Send Ports and Send Port Groups](../core/managing-send-ports-and-send-port-groups.md)