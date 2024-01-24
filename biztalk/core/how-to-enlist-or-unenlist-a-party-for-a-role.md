---
description: "Learn more about: How to Enlist or Unenlist a Party for a Role"
title: "How to Enlist or Unenlist a Party for a Role"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Enlist or Unenlist a Party for a Role
This topic describes how to use the BizTalk Server Administration console to enlist or unenlist a party for a role. Enlisting a party for a role assigns the party to the role and unenlisting the party removes the party from the role.  
  
 When enlisting or unenlisting a party for a role, bear in mind the following points:  
  
-   You must create a party before you can enlist it. For instructions, see [Create a Party](managing-parties.md).  
  
-   You can enlist or unenlist a party for a role without needing to restart the application.  
  
> [!NOTE]
>  The application developer can enlist or unenlist a party during the development process by using the procedure in this topic.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## Enlist or unenlist a party for a role  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the role link for which you want to enlist or unenlist a party.  
  
3. Click **Role Links**, right-click the role link for which you want to enlist or unenlist a party, and then click **Properties**.  
  
4. To enlist a party, do the following:  
  
   -   Click **Enlist** and click the party to enlist.  
  
   -   Click **Bind**, in the **Send Port** drop-down list, click the send port to use for this party, and then click **OK** twice.  
  
5. To unenlist a party, click the party, click **Unenlist**, and then click **OK**.  
  
## See Also  
 [Managing Role Links](../core/managing-role-links.md)
