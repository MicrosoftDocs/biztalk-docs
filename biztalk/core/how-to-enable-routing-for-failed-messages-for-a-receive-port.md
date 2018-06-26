---
title: "How to Enable Routing for Failed Messages for a Receive Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "receive ports, routing"
  - "managing [receive ports], errors"
  - "managing [receive ports], failed messages"
  - "enabling, routing"
  - "messages, failed messages"
  - "routing, messages"
  - "managing [receive ports], routing"
  - "messages, routing"
  - "receive ports, errors"
  - "routing, receive ports"
  - "routing, failed messages"
  - "errors, receive ports"
ms.assetid: 22366664-545d-4981-9bde-4df48b115002
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
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