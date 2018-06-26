---
title: "Stop a Host Instance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c1f2e0c1-a387-4182-82ef-e25f49ac509b
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Stop a Host Instance

## Overview
You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console or Windows Management Instrumentation (WMI) to stop host instances. You must stop a host instance before you can delete it or remove BizTalk Server from a computer. You can stop a host instance that is installed and started. For more information about host instances, see [Host Instances](../core/host-instances.md).  
  
 For information about using WMI to stop a host instance, see **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
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
  
3. In the details pane, right-click the host instance you want to stop, and then click **Stop**.  
  
    The status of the host instance changes to **Stopped**.  
  
   After you stop a host instance, you can start it, delete it, or remove BizTalk Server from the computer. For information about starting a host instance, see [How to Start a Host Instance](../core/how-to-start-a-host-instance.md). For information about deleting a host instance, see [How to Delete a Host Instance](../core/how-to-delete-a-host-instance.md).  
  
## See Also  
 [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md)   
 [How to Add a Host Instance](../core/how-to-add-a-host-instance.md)   
 [How to Start a Host Instance](../core/how-to-start-a-host-instance.md)   
 [How to Delete a Host Instance](../core/how-to-delete-a-host-instance.md)   
 [How to Modify Host Instance Properties](../core/how-to-modify-host-instance-properties.md)