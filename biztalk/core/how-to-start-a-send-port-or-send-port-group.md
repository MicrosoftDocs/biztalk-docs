---
title: "How to Start a Send Port or Send Port Group | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "starting, send port groups"
  - "starting, send ports"
  - "managing [send port groups], starting"
  - "managing [send ports], starting"
  - "send port groups, starting"
  - "send ports, starting"
ms.assetid: f17c0b7c-cad7-4c5e-a08c-3ebf838faa54
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Start a Send Port or Send Port Group
This topic describes how to use the BizTalk Server Administration console to start a send port or send port group. You must start a send port or send port group before it can process messages. If you start an unenlisted send port or send port group, BizTalk enlists the send port or send port group before starting it. A send port group must contain at least one send port in an enlisted state before you can start the send port group. Starting and stopping a send port group does not affect the state of any send ports that it contains.  
  
> [!NOTE]
>  By default, starting a BizTalk application starts all of the artifacts that it contains. For more information, see [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Operators group or the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To start a send port or send port group  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the send port or send port group that you want to start.  
  
3. Click **Send Ports** or **Send Port Groups**, right-click the send port or send port group, and then click **Start**.  
  
## See Also  
 [Managing Send Ports and Send Port Groups](../core/managing-send-ports-and-send-port-groups.md)