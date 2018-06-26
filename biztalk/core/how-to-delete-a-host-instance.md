---
title: "Delete a Host Instance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 35a06480-0962-4bdc-add2-56f979a2f1c9
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Delete a Host Instance

## Overview
You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console or Windows Management Instrumentation (WMI) to delete host instances. For more information about host instances, see [Host Instances](../core/host-instances.md). For information about using WMI to delete a host instance, see **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
 When you delete a host instance, the instance of the BizTalk Server runtime is removed from the associated server and the BizTalk Management database is updated to remove that instance from the host.  
  
 To avoid losing messages when you delete a host instance, BizTalk Server completes all processing before the instance is actually removed.  
  
## Prerequisites  
 To perform this procedure, you must be logged on as a member of the Administrators group and the BizTalk Server Administrators group.  
  
 In addition, you must also be a member of the db_securityadmin SQL Server Database role and the securityadmin SQL Server Role on the server(s) where the following databases are:  
  
-   BAM Primary Import (BAMPrimaryImport)  
  
-   BizTalk Management (BizTalkMgmtDb)  
  
-   BizTalk MessageBox (BizTalkMsgBoxDb) (all)  
  
-   BizTalk Tracking (BizTalk DTADb)  
  
-   Rule Engine (BizTalkRuleEngineDb)  
  
> [!CAUTION]
>  We recommend that you update account information for host instances by using the BizTalk Server Administration Console or a Windows Management Instrumentation (WMI) script. This ensures that BizTalk Server can update the account information in the BizTalk Server databases and keep the security configuration between the databases and host instance synchronized.  
  
## Steps
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, click **Platform Settings**, and then click **Host Instances**.  
  
3. In the details pane, right-click the host instance you want to delete, and then click **Delete**.  
  
4. In the **Confirm delete host instance** dialog box, click **Yes**.  
  
   > [!NOTE]
   >  If BizTalk Server cannot delete the host instance, a dialog box appears in which you can force the deletion of the host instance. After reading the information provided, click **Yes** to delete the host instance.  
  
## See Also  
 [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md)   
 [How to Add a Host Instance](../core/how-to-add-a-host-instance.md)   
 [How to Start a Host Instance](../core/how-to-start-a-host-instance.md)   
 [How to Stop a Host Instance](../core/how-to-stop-a-host-instance.md)   
 [How to Modify Host Instance Properties](../core/how-to-modify-host-instance-properties.md)