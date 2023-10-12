---
description: "Learn more about: How to Configure Authentication Options for a Receive Port"
title: "How to Configure Authentication Options for a Receive Port"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Configure Authentication Options for a Receive Port
This topic describes how to use the BizTalk Server Administration console to configure message authentication options for a receive port. These options take effect when party resolution authentication is configured. The options are:  
  
- **No authentication.** If this option is selected, the receive port will pass the message through without checking for message credentials.  
  
- **Drop messages if authentication fails.** If this option is selected, the receive port will check message credentials using Party resolution and discard the message if authentication fails.  
  
- **Keep messages if authentication fails.** If this option is selected, the receive port will check message credentials using Party resolution and keep the message in the suspended queue if authentication fails.  
  
  For instructions on creating and configuring a party, see [Create a Party](managing-parties.md). For more information about party resolution authentication, see [Authenticating the Sender of a Message](../core/authenticating-the-sender-of-a-message.md) and [Inbound Message Authentication](../core/inbound-message-authentication.md).  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## Configure authentication options for a receive port  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure authentication for a receive port.  
  
3. Click **Receive Ports**, right-click the receive port, and then click **Properties**.  
  
4. In the **Authentication** section, select the option you want, and then click **OK**.  
  
## See Also  
 [Managing Receive Ports](../core/managing-receive-ports.md)
