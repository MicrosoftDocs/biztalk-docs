---
title: "How to Enlist a Send Port or Send Port Group | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "enlisting, send port groups"
  - "enlisting, send ports"
  - "send port groups, enlisting"
  - "send ports, enlisting"
  - "managing [send ports], enlisting"
  - "managing [send port groups], enlisting"
ms.assetid: d4298b8e-7dc7-4382-af86-c4db0982b7e0
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Enlist a Send Port or Send Port Group
This topic describes how to use the BizTalk Server Administration console to enlist a send port or send port group. Enlisting a send port or send port group associates the send port or send port group with a BizTalk host and creates the subscriptions for the send port or send port group. If a send port group does not contain a send port, enlisting the send port group does not create any subscriptions. In addition, enlisting a send port group does not change the state of any send ports that it contains.  
  
> [!NOTE]
>  Starting a send port or send port group also automatically enlists it. In addition, by default starting an application enlists and starts all of its artifacts. For more information, see [How to Start a Send Port or Send Port Group](../core/how-to-start-a-send-port-or-send-port-group.md). Also see [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To enlist a send port or send port group  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the send port or send port group that you want to enlist.  
  
3. Click **Send Ports** or **Send Port Groups**, right-click the send port or send port group, and then click **Enlist**.  
  
## See Also  
 [Managing Send Ports and Send Port Groups](../core/managing-send-ports-and-send-port-groups.md)