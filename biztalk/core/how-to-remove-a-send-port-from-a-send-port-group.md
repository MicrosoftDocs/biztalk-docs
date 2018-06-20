---
title: "How to Remove a Send Port from a Send Port Group | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "send port groups, deleting send ports"
  - "managing [send port groups], deleting send ports"
  - "managing [send ports], deleting send ports"
  - "deleting, send ports"
  - "send ports, deleting from send port groups"
ms.assetid: a2289bfe-5bc9-4bc7-949c-5152ffb5bc62
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Remove a Send Port from a Send Port Group
This topic describes how to use the BizTalk Server Administration console to remove a send port from a send port group. When you do this, the send port is not deleted from the application or the BizTalk Management database.  
  
 Before you can remove a send port, it must be in a stopped or unenlisted state.  
  
> [!NOTE]
>  To route messages, a send port group must contain at least one send port.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To remove a send port from a send port group  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application in which you want to remove a send port from a send port group.  
  
3. Click **Send Port Groups**, right-click the send port group, and then click **Properties**.  
  
4. Under **Name**, click the send port to remove, and then click **Remove**.  
  
## See Also  
 [Creating and Configuring Send Port Groups](../core/creating-and-configuring-send-port-groups.md)   
 [Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md)