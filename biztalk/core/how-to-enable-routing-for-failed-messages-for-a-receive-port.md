---
description: "Learn more about: How to Enable Routing for Failed Messages for a Receive Port"
title: "How to Enable Routing for Failed Messages for a Receive Port"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Enable Routing for Failed Messages for a Receive Port
This topic describes how to use the BizTalk Server Administration console to enable routing for the messages processed by a receive port. When you enable this option, BizTalk Server will attempt to route any message that fails processing to a subscribing application (such as another receive port or orchestration schedule). When this option is not enabled (the default), BizTalk Server suspends failed messages and generates a negative acknowledgment (NACK). For background information about managing failed messages, see [Using Failed Message Routing](../core/using-failed-message-routing.md).  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To enable routing for failed messages for a receive port  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure failed message routing for a receive port.  
  
3. Click **Receive Ports**, right-click the receive port, and then click **Properties**.  
  
4. Select the **Enable routing for failed messages** check box, and then click **OK**.  
  
## See Also  
 [Managing Receive Ports](../core/managing-receive-ports.md)
