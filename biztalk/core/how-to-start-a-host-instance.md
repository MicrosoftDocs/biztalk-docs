---
title: "Start a Host Instance | Microsoft Docs"
description: Use BizTalk Administration to start a host instance in BizTalk Server
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a96a4362-2147-4b8e-a270-bf9a17477ba3
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Start a Host Instance
You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console or Windows Management Instrumentation (WMI) to start host instances. After you add or stop a host instance, you must start it so that it is running and routing messages to the MessageBox databases.  
  
> [!IMPORTANT]
>  The service account that you specify for a host instance should be a member of the Windows group for the associated host. Otherwise, the host instance may not have the appropriate permissions or authentication at run time. In addition, for security reasons, the account should have minimum privileges because orchestrations hosted by the host instance might execute potentially malicious custom code.  
  
 For more information about host instances, see [Host Instances](../core/host-instances.md). For information about using WMI to start a host instance, see **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
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
  
3. In the details pane, right-click the host instance you want to start, and then click **Start**.  
  
    The status of the host instance changes to **Start pending**. After the host instance initiates, the status changes to **Running**.  
  
   After you start a host instance, you can stop it to prevent it from routing messages to the MessageBox database. You must stop a host instance before you can remove BizTalk Server from a given computer. For information about stopping a host instance, see [How to Stop a Host Instance](../core/how-to-stop-a-host-instance.md).  
  
## See Also  
 [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md)   
 [Add a Host Instance](../core/how-to-add-a-host-instance.md)   
 [Stop a Host Instance](../core/how-to-stop-a-host-instance.md)   
 [Delete a Host Instance](../core/how-to-delete-a-host-instance.md)   
 [Modify Host Instance Properties](../core/how-to-modify-host-instance-properties.md)