---
title: "Disable New Message Publication | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9099ecaa-31ed-4880-a0f6-8dbfaf783f7a
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Disable New Message Publication

## Overview
You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console or Windows Management Instrumentation (WMI) to disable new message publication. You disable new message publication in the MessageBox database to stop the receipt of new messages by the MessageBox database. In some BizTalk Server environments, you can improve performance if you disable new message publication for the master MessageBox database. Disabling new message publication does not affect existing messages in the MessageBox database or service instances that are in progress.  
  
 For information about using WMI to disable new message publication, see the **MSBTS_MsgBoxSetting.DisableNewMessagePublication Property (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
> [!IMPORTANT]
>  You must disable the publication of new messages before you delete a MessageBox database. For information about deleting a MessageBox database, see [How to Delete a MessageBox Database](../core/how-to-delete-a-messagebox-database.md).  
  
## Prerequisites  
 Administrators who manage MessageBox databases must have the required user rights. You must have the following user rights to manage MessageBox databases and disable new message publication:  
  
-   You must be logged on as a member of the BizTalk Server Administrators group.  
  
-   You must be a SQL Server Administrator on the computer where the database exists.  
  
## Disable steps
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, click **Platform Settings**, and then click **Message Boxes**.  
  
3. In the details pane, right-click the MessageBox database you want to disable, and then click **Properties**.  
  
4. In the **Message Box Properties** dialog box, select the **Disable new message publication** check box, and then click **OK**.  
  
## See Also  
 [Managing MessageBox Databases](../core/managing-messagebox-databases.md)   
 [Add a New MessageBox Database](../core/how-to-add-a-new-messagebox-database.md)   
 [Delete a MessageBox Database](../core/how-to-delete-a-messagebox-database.md)   
 [The MessageBox Database](../core/the-messagebox-database.md)