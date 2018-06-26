---
title: "How to Create a Send Port Group | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating, send port groups"
  - "send port groups, creating"
  - "managing [send port groups], creating"
ms.assetid: de3e72aa-83f4-4760-9f39-a488f904f1d3
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create a Send Port Group
This topic describes how to use the BizTalk Server Administration console to create a send port group in a BizTalk application and then add send ports to it. You can add static one-way send ports only to a send port group. A send port group must contain at least one send port to route messages.  
  
 You can add a send port that exists in a different application. If you do this, you must add a reference from the application containing the send port group to the application containing the send port. For instructions, see [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To create a send port group  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application in which you want to create a send port group.  
  
3. Right-click **Send Port Groups**, point to **New**, and then click **Send Port Group**.  
  
4. In the **Name** box, type a name for the send port group.  
  
5. In **Send ports**, click the drop-down list under **Name**, and click the send port to add to the send port group. Repeat for each send port you want to add to the group. To create a new send port and add it, click **\<New send port…\>** and then follow the instructions in [How to Create a Send Port](../core/how-to-create-a-send-port2.md).  
  
6. When finished adding send ports to the send port group, click **OK**.  
  
## See Also  
 [Creating and Configuring Send Port Groups](../core/creating-and-configuring-send-port-groups.md)