---
title: "How to Add a Send Port to a Send Port Group | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [send port groups], adding send ports"
  - "managing [send ports], adding to send port groups"
  - "send port groups, send ports"
  - "send ports, send port groups"
  - "adding, send ports"
ms.assetid: a61b3b32-c05e-40b9-abf1-09b7065fb6a2
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add a Send Port to a Send Port Group
This topic describes how to use the BizTalk Server Administration console to add one or more send ports to a send port group. You can only add one-way static send ports to a send port group.  
  
 You can add a send port that exists in a different application. If you do this, you must add a reference from the application containing the send port group to the application containing the send port. For instructions, see [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To add a send port to a send port group  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application in which you want to add a send port to a send port group.  
  
3. Click **Send Port Groups**, right-click the send port group, and then click **Properties**.  
  
4. In **Send ports**, click the drop-down list under **Name**, and click the send port to add to the send port group. Repeat for each send port you want to add to the group. To create a new send port and add it, click **\<New send port…\>** and then follow the instructions in [How to Create a Send Port](../core/how-to-create-a-send-port2.md).  
  
5. When finished adding send ports to the send port group, click **OK**.  
  
## See Also  
 [Creating and Configuring Send Port Groups](../core/creating-and-configuring-send-port-groups.md)   
 [Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md)