---
title: "How to Unenlist a Send Port or Send Port Group | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "unenlisting, send port groups"
  - "send port groups, unenlisting"
  - "managing [send ports], unenlisting"
  - "managing [send port groups], unenlisting"
  - "unenlisting, send ports"
  - "send ports, unenlisting"
ms.assetid: 3185adad-2efa-4abd-a532-77ae6c7b4c1d
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Unenlist a Send Port or Send Port Group
This topic describes how to use the BizTalk Server Administration console to unenlist a send port or send port group. Unenlisting a send port or send port group eliminates all subscriptions associated with that send port or send port group. You can unenlist both running and stopped send ports or send port groups. Unenlisting a send port or send port group automatically stops it.  
  
 For example, you may want to unenlist a send port or send port group to edit its bindings, or if you want to remove the send port or send port group from the BizTalk Server environment.  
  
 You cannot unenlist the last enlisted send port within a send port group that is enlisted or running. Unenlisting a send port group does not change the state of any send ports that it contains.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To unenlist a send port or send port group  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the send port or send port group that you want to unenlist.  
  
3. Click **Send Ports** or **Send Port Groups**, right-click the send port or send port group, and then click **Unenlist**.  
  
## See Also  
 [Managing Send Ports and Send Port Groups](../core/managing-send-ports-and-send-port-groups.md)