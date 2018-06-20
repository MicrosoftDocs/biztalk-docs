---
title: "How to Delete a Send Port Group | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "send port groups, deleting"
  - "managing [send port groups], deleting"
  - "deleting, send port groups"
ms.assetid: 90c01e58-d35c-4cb2-ac6d-92199199fb42
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Delete a Send Port Group
This topic describes how use the BizTalk Server Administration console to delete a send port group from a BizTalk application. When you do this, the send port group is also deleted from the BizTalk Management database for the group. Deleting a send port group does not delete any send ports that it contains.  
  
 You can delete a send port group only if it meets the following conditions:  
  
-   An orchestration is not bound to the send port group. If this is the case, you can remove the binding by following the instructions in [How to Unbind an Orchestration](../core/how-to-unbind-an-orchestration.md).  
  
-   The send port group is both stopped and unenlisted. For instructions on stopping and unenlisting a send port, see [How to Unenlist a Send Port or Send Port Group](../core/how-to-unenlist-a-send-port-or-send-port-group.md) and [How to Stop a Send Port or Send Port Group](../core/how-to-stop-a-send-port-or-send-port-group.md).  
  
-   The send port group is not referenced by a party. For instructions on removing a reference to a send port group from a party, see [How to View or Edit a Party](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca).  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To delete a send port group  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, expand **Applications**, and then expand the application containing the send port group that you want to delete.  
  
3. Click **Send Port Groups**, right-click the send port group, and then click **Delete**.  
  
## See Also  
 [Creating and Configuring Send Port Groups](../core/creating-and-configuring-send-port-groups.md)