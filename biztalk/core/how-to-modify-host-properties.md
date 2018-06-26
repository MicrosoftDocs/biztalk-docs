---
title: "How to Modify Host Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5df9d7f-b6c2-4bb7-a845-284e6323e3d6
caps.latest.revision: 28
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Update Host Properties

## Overview
You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to modify the following host properties:  

-   **Windows group:** Members of the Windows group have permissions to run the hosts instances of this host by default. When you select a Windows user group for a BizTalk Host, we recommend that you create a new group that is dedicated to that host. If you do use an existing group, ensure that the group does not have more privileges than are needed. For more information, see [Access Control and Data Security](../core/access-control-and-data-security.md).  

    > [!NOTE]
    >  If you change the group membership of the current logged-in user, and the group is also a member of the domain, you should logout and login after changes are completed. Failure to do this will result in denied access because new group membership will not be reflected by the current login.  

-   **Host tracking:** At least one host in the group must track health and business data. This option indicates whether the host loads the BizTalk Tracking component to process health monitoring and business data.  

    > [!NOTE]
    >  We recommend that you create at least one host instance of the tracking host. If there is no running host instance of the tracking host, the MessageBox database will continue to accumulate data with a subsequent degradation in performance.  

     The host that performs host tracking has read/write access to the tracking tables in the MessageBox database, as well as access to the BizTalk Tracking database. Therefore, any objects running in a host that performs host tracking also have read/write access to these database tables. Hosts that do not perform host tracking have only write access to the tracking tables in the MessageBox database, and do not have access to the BizTalk Tracking database.  

    > [!NOTE]
    >  Specifying a particular host to perform host tracking will have an impact on the performance of applications running on the same host. Therefore, you might want to consider creating a dedicated host just to "allow host tracking" for this reason.  

-   **Authentication trusted:** You can specify that BizTalk Server trusts a host. BizTalk Server trusts **authentication trusted hosts** to place the sender security ID (SSID) on messages that the trusted host is queuing that map to users other than to the host. For more information about authentication trusted hosts, see [Authenticating the Sender of a Message](../core/authenticating-the-sender-of-a-message.md).  

     Host instances of trusted hosts and host instances of non-trusted hosts cannot use the same service accounts. If you want to change the trust setting of a host instance and the host instance uses a service account that other host instances use, you can do one of the following:  

    -   You can change the service account of the host instance for which you want to change the trust settings to a new service account.  

    -   You can change the service account of the host instance to an existing service account that other host instances with the same trust setting use.  

    -   You can delete the host instance, and re-create it with a different trust setting and service account.  

-   **Default host in the group:** There must be a default host in the group at all times. The orchestration enlistment process automatically uses the default host to host the orchestration, unless the user explicitly selects a different host. The first host created is marked as the default host. For information about the default host, see [Hosts](../core/hosts.md).  

## Prerequisites  
 You must have the following user rights to create hosts, modify host properties, and delete hosts:  

-   You must be a member of the BizTalk Server Administrators group. For information about adding users to the BizTalk Server Administrators group, see [How to Manage the BizTalk Server Administrators Group](../core/how-to-manage-the-biztalk-server-administrators-group.md).  

-   You must have the following rights in SQL Server:  

    -   You must be either a SQL Server administrator, or a member of the db_owner or db_securityadmin SQL Server database roles in the BizTalk Tracking database (BizTalk DTADb), MessageBox databases (BizTalkMsgBoxDb), and the BAM Primary Import database (BAMPrimaryImport).  

    -   You must be a member of the sysadmin SQL Server role on all the computers where there are MessageBox databases, or a member of the db_owner or db_ddladmin SQL Server role for all the MessageBox databases.  

## Steps  

1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  

2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, click **Platform Settings**, and then click **Hosts**.  

3. In the details pane, right click the host you want to modify and then click **Properties**.  

4. In the **Host Properties** dialog box, on the **General** tab, do the following:  

   |Use this|To do this|  
   |--------------|----------------|  
   |**Name**|Displays the name of the host. You name the host when you create it.|  
   |**Type**|Displays the host type. You can enlist an orchestration to an In-process host, and an In-process host can host a send handler. An Isolated host operates outside the BizTalk Server installation.|  

    **Options**  


   |                  Use this                   |                                                                                                                                                                                                                                                                                    To do this                                                                                                                                                                                                                                                                                    |
   |---------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |           **Allow Host Tracking**           | Select this check box to indicate that the host loads the BizTalk Tracking component to process health monitoring and business data. If you select this check box, the current host will have read/write access to the tracking tables in the MessageBox database, as well as to the Tracking database. Accordingly, any objects running in this host will also have read/write access to these databases. If you clear the check box, the host will have only write access to the tracking tables in the MessageBox database and will not have access to the Tracking database. |
   |         **Authentication Trusted**          |                                                                                                                                                                                                                                                   Select this check box to specify that BizTalk Server should trust this host.                                                                                                                                                                                                                                                   |
   |               **32-bit only**               |                     Select this check box if you want the host instance process to be created as 32-bit on both 32-bit and 64-bit servers. If this check box is cleared, the host instance process will be created as 32-bit on 32-bit servers and as 64-bit on 64-bit servers.<br /><br /> **Note** To change a 32-bit host instance process into a 64-bit host instance process, delete all instances of the host, and then clear the **32-bit only** check box. When you create instances of the host on a 64-bit server, they will be created as 64-bit.                     |
   | **Make this the default host in the group** |                                                                                                                                           Select this check box to identify this host as the default host. The orchestration enlistment process automatically uses the default host to host the orchestration, unless you explicitly select a different host. If this check box is selected and unavailable, this host is the default.                                                                                                                                           |
   |              **Windows group**              |                                                                                                                                                                                                                          Type the local or domain group for the host. Members of the Windows group will have permissions to run instances of this host.                                                                                                                                                                                                                          |


5. On the **Certificates** tab, do the following, and then click **OK**:  

   |Use this|To do this|  
   |--------------|----------------|  
   |**Description**|Displays a description of the displayed decryption certificate.|  
   |**Thumbprint**|Displays the thumbprint of the private key certificate used to decrypt inbound messages for this host. The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit (a number from 0 through 9 or a letter from A through F).|  
   |**Remove certificate**|Click to remove the displayed decryption certificate from the host.|  
   |**Browse**|Click to display the **Select Certificate** dialog box, where you select the decryption certificate from the Local Machine or Other People certificate store that you want to use with the host.|  

## See Also  
- [Optimizing Resource Usage Through Host Throttling](../core/optimizing-resource-usage-through-host-throttling.md)   
- [Throttling Design Recommendations](../core/throttling-design-recommendations.md)   
- [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md)   
- [How to Create a New Host](../core/how-to-create-a-new-host.md)   
- [How to Delete a Host](../core/how-to-delete-a-host.md)   
- **MSBTS_Host (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
