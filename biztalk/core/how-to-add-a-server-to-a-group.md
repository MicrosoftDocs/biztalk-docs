---
title: "How to Add a Server to a Group | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "groups, servers"
  - "adding, servers"
  - "managing [groups], adding servers"
  - "servers, groups"
  - "managing [servers], adding to groups"
ms.assetid: 6eca1eeb-1a56-4470-b3bc-c64865cf6270
caps.latest.revision: 26
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add a Server to a Group
You can use BizTalk Server Configuration to add a server to a BizTalk group. You add additional servers to a BizTalk group to scale out your BizTalk Server environment.  
  
 A server can only be associated with one BizTalk group. If a server already belongs to another group, you must first remove that server from its current group before you can add it to a new group. For information about removing a server from a BizTalk group, see [How to Remove a Server from a Group](../core/how-to-remove-a-server-from-a-group.md).  
  
> [!NOTE]
>  BizTalk groups associated with different servers in a BizTalk Server environment do not interact except to exchange messages.  
  
> [!IMPORTANT]
>  The BizTalk Server runtime must be installed on the computer you want to add to the BizTalk group.  
  
## Prerequisites  
 To perform this procedure, you must be logged on as a member of the SSO Administrators group and as a member of the Windows Administrators group.  
  
### To add a server to a BizTalk group  
  
1. On the computer that you want to add to a BizTalk Server group to, click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.  
  
2. In **Microsoft BizTalk Server Configuration**, select **Custom configuration**.  
  
3. In **Database server name**, type the name of the SQL Server for the BizTalk Group the server is joining.  
  
4. In **Service credential**, type the appropriate user name and password that the services will use, and then click **Configure**.  
  
5. In the navigation tree on the left side of the screen, click **Enterprise SSO**.  
  
6. On the **Enterprise Single Sign-On** page, click **Join an existing SSO system**.  
  
    Ensure that the server name and database name point to the master SSO database server for the BizTalk Server group the server is joining.  
  
7. In the navigation tree on the left side of the screen, click **Group**.  
  
8. On the **Group** page, click **Join an existing BizTalk Group**.  
  
    Ensure that the server name and database name point to the databases for the BizTalk Server group the server is joining.  
  
9. On the menu bar, click **Apply Configuration** to configure both Enterprise Single Sign-On and the Group on this computer.  
  
## See Also  
 [Working with the Configuration Framework](../install-and-config-guides/working-with-the-configuration-framework.md)   
 [Managing Groups](../core/managing-groups.md)   
 [BizTalk Groups](../core/biztalk-groups.md)   
 [How to Move a Server from One Group to Another](../core/how-to-move-a-server-from-one-group-to-another.md)   
 [How to Remove a Server from a Group](../core/how-to-remove-a-server-from-a-group.md)   
 [How to Modify Group Properties](../core/how-to-modify-group-properties.md)   
 [Managing Servers](../core/managing-servers.md)