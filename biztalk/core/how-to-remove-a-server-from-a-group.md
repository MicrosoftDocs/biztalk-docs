---
description: "Learn more about: How to Remove a Server from a Group"
title: "How to Remove a Server from a Group"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Remove a Server from a Group
A server can only be associated with one BizTalk group. If a server already belongs to another group, you must first remove that server from its current group before you can add it to a new group.  
  
## Prerequisites  
 To perform this procedure, you must be logged on as a member of the Windows Administrators group.  
  
### To remove a server from a group  
  
1. On the computer that you want to remove from a BizTalk Server group, click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.  
  
2. On the menu bar, click **Unconfigure Features**.  
  
3. In the **Unconfigure Features** dialog box, select **Group**, and then click **OK**.  
  
   > [!CAUTION]
   >  Unconfiguring a group will also unconfigure all dependent features that are already configured on that computer.  
  
4. Click **Yes**.  
  
5. In the Microsoft BizTalk Server Configuration Wizard, click **Next**.  
  
    The Group and its dependent features are unconfigured.  
  
6. Click **Finish**.  
  
## See Also  
 [Managing Groups](../core/managing-groups.md)   
 [BizTalk Groups](../core/biztalk-groups.md)   
 [How to Add a Server to a Group](../core/how-to-add-a-server-to-a-group.md)   
 [How to Move a Server from One Group to Another](../core/how-to-move-a-server-from-one-group-to-another.md)   
 [How to Modify Group Properties](../core/how-to-modify-group-properties.md)   
 [Managing Servers](../core/managing-servers.md)
