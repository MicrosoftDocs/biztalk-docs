---
title: "Create a New Host | Microsoft Docs"
descriptions: Use BizTalk Administration to create a new host in BizTalk Server
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 811e6e57-5c37-471a-aff4-5b2b68c367b1
caps.latest.revision: 27
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Create a New Host
A BizTalk Host is a logical container for items such as adapter handlers, receive locations (including pipelines), and orchestrations. We recommend that you use separate hosts for processing, receiving, and sending messages, and that you use separate hosts for trusted and non-trusted items to facilitate implementing security measures and to improve manageability of the hosts. You can install only one instance of a host per BizTalk server. For more information about hosts, see [Hosts](../core/hosts.md).  

 For information about using Windows Management Instrumentation (WMI) to create a new host, see **MSBTS_Host (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

## Prerequisites  
 You must have the following user rights to create hosts, modify host properties, and delete hosts:  

-   You must be a member of the BizTalk Server Administrators group.  

-   You must have the following rights in SQL Server:  

    -   You must be either a SQL Server administrator, or a member of the db_owner or db_securityadmin SQL Server database roles in the BizTalk Tracking (BizTalk DTADb) database, MessageBox (BizTalkMsgBoxDb) databases, and the BAM Primary Import (BAMPrimaryImport) database.  

    -   You must be a member of the sysadmin SQL Server role on all the computers where there are MessageBox databases, or a member of the db_owner or db_ddladmin SQL Server role for all the MessageBox databases.  

## Steps

1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  

2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, click **Platform Settings**, and then click **Hosts**.  

3. In the details pane, right click **Hosts**, click **New**, and then click **Host**.  

4. In the **Host Properties** dialog box, on the **General** tab, do the following:  

   |Use this|To do this|  
   |--------------|----------------|  
   |**Name**|Displays the name of the host. You name the host when you create it. The host name cannot exceed 80 characters in length.|  
   |**Type**|Displays the host type. An In-process Host can host orchestrations, certain send handlers and receive handlers. An Isolated Host is a process boundary outside of BizTalk Server and is required by certain send and receive handlers. You can enlist an orchestration to an In-process host, and an In-process host can host a send or receive handler.|  

    **Options**  


   |                  Use this                   |                                                                                                                                                                                                                                                                            To do this                                                                                                                                                                                                                                                                             |
   |---------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |           **Allow Host Tracking**           | Select this check box to indicate that the host will process health monitoring and business data. If you select this check box, the current host will have read/write privileges to the tracking tables in the MessageBox database, as well as to the BizTalk Tracking database. Accordingly, any objects running in this host will also have read/write access to these databases. If you clear the check box, the host will have only write access to the tracking tables in the MessageBox database and will not have access to the BizTalk Tracking database. |
   |         **Authentication Trusted**          |                                                                                                                                                                                                                                           Select this check box to specify that BizTalk Server should trust this host.                                                                                                                                                                                                                                            |
   |               **32-bit only**               |                                                                                                                                               Select this check box if you want to allow the host instance process to be created as 32-bit on both 32-bit and 64-bit servers. If this check box is cleared, the host instance process will be created as 32-bit on 32-bit servers and as 64-bit on 64-bit servers.                                                                                                                                                |
   | **Make this the default host in the group** |                                                                                                                                      Select this check box to identify this host as the default host. Created ports and orchestrations automatically use the default host to host the orchestration, unless you explicitly select a different host. If this check box is selected and unavailable, this host is the default.                                                                                                                                      |
   |              **Windows group**              |                                                                                                                                                                                                                  Type the local or domain group for the host. Members of the Windows group will have permissions to run instances of this host.                                                                                                                                                                                                                   |


5. On the **Certificates** tab, do the following, and then click **OK**:  

   |Use this|To do this|  
   |--------------|----------------|  
   |**Common Name**|Displays a description of the displayed decryption certificate.|  
   |**Thumbprint**|Displays the thumbprint of the private key certificate used to decrypt inbound messages for this host. The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit (a number from 0 through 9 or a letter from A through F).|  
   |**Remove certificate**|Click to remove the displayed decryption certificate from the host.|  
   |**Browse**|Click to display the **Windows Security** dialog box, where you select the decryption certificate from the current user or personal store that you want to use with the host.|  

## See Also  
 [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md)   
 [Modify Host Properties](../core/how-to-modify-host-properties.md)   
 [Delete a Host](../core/how-to-delete-a-host.md)