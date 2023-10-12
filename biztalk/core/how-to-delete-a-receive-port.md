---
description: "Learn more about: How to Delete a Receive Port"
title: "How to Delete a Receive Port"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Delete a Receive Port
This topic describes how to use the BizTalk Server Administration console to delete a receive port from a BizTalk application. When you do this, the receive port is also deleted from the BizTalk Management database for the group, as are all receive locations in this receive port.  
  
 For this operation to succeed, the receive port cannot be bound to an orchestration. For instructions on removing the bindings for a receive port, see [How to Unbind an Orchestration](../core/how-to-unbind-an-orchestration.md).  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To delete a receive port  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, expand **Applications**, and then expand the application containing the receive port that you want to delete.  
  
3. Click **Receive Ports**, right-click the receive port, and then click **Delete**.  
  
## See Also  
 [Managing Receive Ports](../core/managing-receive-ports.md)
