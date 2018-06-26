---
title: "Delete a Host | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e3df8719-27cb-4010-82e3-68226ab74b17
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Delete a Host
You can delete a host only in the following circumstances:  

- It is not the default host.  

- It is not the only host that is performing host tracking.  

- It is not hosting any adapter handlers.  

- It has no enlisted orchestrations.  

- There are no started instances of the host.  

- If the host is not clustered.  

  For more information about hosts, see [Hosts](../core/hosts.md).  

## Prerequisites  
 You must have the following user rights to create hosts, modify host properties, and delete hosts:  

-   You must be a member of the BizTalk Server Administrators group.  

-   You must have the following rights in SQL Server:  

    -   You must be either a SQL Server administrator, or a member of the db_owner or db_securityadmin SQL Server database roles in the BizTalk Tracking database (BizTalk DTADb), MessageBox databases (BizTalkMsgBoxDb), and the BAM Primary Import database (BAMPrimaryImport).  

    -   You must be a member of the sysadmin SQL Server role on all the computers where there are MessageBox databases, or a member of the db_owner or db_ddladmin SQL Server role for all the MessageBox databases.  

## Steps 

1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  

2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, click **Platform Settings**, and then click **Hosts**.  

3. In the details pane, right-click the host you want to delete, and then click **Delete**.  

4. In the **Confirm host delete** dialog box, click **Yes**.  

## See Also  
- [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md)   
- [How to Create a New Host](../core/how-to-create-a-new-host.md)   
- [How to Modify Host Properties](../core/how-to-modify-host-properties.md)   
- **MSBTS_Host (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
