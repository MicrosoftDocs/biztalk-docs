---
title: "How to Move a Server from One Group to Another | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "groups, servers"
  - "groups, moving"
  - "managing [groups], moving servers"
  - "servers, moving"
  - "managing [servers], moving"
  - "servers, groups"
ms.assetid: 3f789a62-f597-426b-9cea-74c1fe22b694
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Move a Server from One Group to Another
A server can only be associated with one BizTalk Server group. To move a server from one group to another, you must first remove the server from the original group by unconfiguring it, and then add the server to the new group.  
  
## Prerequisites  
 To perform this procedure, you must be logged on as a member of the SSO Administrators group and as a member of the Windows Administrators group.  
  
### To move a server from one BizTalk group to another  
  
1. On the computer that you want to move from the BizTalk group to another, click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.  
  
2. On the menu bar, click **Unconfigure Features**.  
  
3. In the **Unconfigure Features** dialog box, select **Enterprise SSO**, select **Group**, and then click **OK**.  
  
   > [!CAUTION]
   >  Unconfiguring a group will also unconfigure all dependent features that are already configured on that computer.  
  
4. Click **Yes**.  
  
5. In the **Microsoft BizTalk Server Configuration** window, click **Next**.  
  
    Enterprise SSO, the Group, and their dependent features are unconfigured.  
  
6. Click **Finish**.  
  
7. In the **Microsoft BizTalk Server Configuration** window, select **Custom configuration**.  
  
8. In **Database server name**, type the name of the SQL server for the BizTalk Group where you are moving the server.  
  
9. In **Service credential**, type the appropriate user name and password that the services will use, and then click **Configure**.  
  
10. In the navigation tree on the left side of the screen, click **Enterprise SSO**.  
  
11. On the **Enterprise Single Sign-On** page, click **Join an existing SSO system**.  
  
     Ensure that the server name and database name point to the master SSO database server for the BizTalk Server group where you are moving the server.  
  
12. In the navigation tree on the left side of the screen, click **Group**.  
  
13. On the **Group** page, click **Join an existing BizTalk Group**.  
  
     Ensure that the server name and database name point to the databases for the BizTalk Server group where you are moving the server.  
  
14. On the menu bar, click **Apply Configuration** to configure both Enterprise Single Sign-On and the Group on this computer.  
  
## See Also  
 [Managing Groups](../core/managing-groups.md)   
 [BizTalk Groups](../core/biztalk-groups.md)   
 [How to Add a Server to a Group](../core/how-to-add-a-server-to-a-group.md)   
 [How to Remove a Server from a Group](../core/how-to-remove-a-server-from-a-group.md)   
 [How to Modify Group Properties](../core/how-to-modify-group-properties.md)   
 [Working with the Configuration Framework](../install-and-config-guides/working-with-the-configuration-framework.md)   
 [How to Add a Host Instance](../core/how-to-add-a-host-instance.md)   
 [Managing Servers](../core/managing-servers.md)