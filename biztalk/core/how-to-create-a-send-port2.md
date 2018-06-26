---
title: "How to Create a Send Port2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.procedure.createsendport"
helpviewer_keywords: 
  - "managing [send ports], creating"
  - "creating, send ports"
  - "send ports, creating"
ms.assetid: 7f0d07b8-1ac5-4032-bb08-2f7e05185f86
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create a Send Port
This topic describes how to use the BizTalk Server Administration console to create a send port. When creating a send port, you must select the type of send port to create, as follows:  

- Static one-way — a send-only port.  

- Static solicit-response — a send port that waits for a reply from the destination.  

- Dynamic one-way — a send-only port that can be bound to a protocol and location at runtime based on message properties.  

- Dynamic solicit-response — a send port that waits for a reply and can be bound to a protocol and location at runtime based on message properties.  

  After you create a send port, you can perform the following additional steps to complete the configuration:  

- Configure advanced transport options, such as the number of times to retry sending messages on message failure and the service window schedule for the port, as described in [How to Configure Transport Advanced Options for a Send Port](../core/how-to-configure-transport-advanced-options-for-a-send-port.md).  

- Configure a backup transport, in the event the primary transport fails to function, as described in [How to Configure Backup Transport Options for a Send Port](../core/how-to-configure-backup-transport-options-for-a-send-port.md).  

- Configure filters to determine which messages are routed to this send port from the message box, as described in [How to Configure Filters for a Send Port](../core/how-to-configure-filters-for-a-send-port.md).  

- Assign a security certificate to the send port to encrypt or sign documents handled by the send port, as described in [How to Assign a Certificate to a Send Port](../core/how-to-assign-a-certificate-to-a-send-port.md).  

- Configure tracking options for messages handled by the send port, as described in [How to Configure Tracking for a Send Port](../core/how-to-configure-tracking-for-a-send-port.md).  

## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md). In addition, you need to have SSO affiliate administrator permissions on the Enterprise Single Sign-On (SSO) database. For more information, see [SSO User Groups](../core/sso-user-groups.md).  

### To create a send port  

1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  

2. In the console tree, expand the BizTalk group and the BizTalk application for which you want to create a send port.  

3. Right-click **Send Ports**, point to **New**, and then click the type of port to create.  

4. In the **Send Ports Properties** window, do the following:  


   |       Use this       |                                                                                                                                                                                                                                To do this                                                                                                                                                                                                                                 |
   |----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |       **Name**       |                                                                                                                                                                                            Type the name of the new send port. This name must be unique in the BizTalk group.                                                                                                                                                                                             |
   |  **Transport Type**  |                                                                                                       From the drop-down list, select the appropriate transport type, or transport protocol. If the port is a solicit-response port, only transport types that support solicit-response are available in the list. This property is visible only for static ports.                                                                                                        |
   |    **Configure**     |                                                                                          After you select the transport type, click **Configure** to display the **Transport Properties** dialog box, which provides transport-specific configuration options. This property is visible only for static ports. Click **Help** in the dialog box for configuration instructions.                                                                                           |
   |   **Send handler**   |                                                                                                                                                                  From the drop-down list, select the host instance on which the send adapter is running. This property is visible only for static ports.                                                                                                                                                                  |
   |  **Send pipeline**   |                                            From the drop-down list, select the pipeline that processes the messages sent through this port. After you select the pipeline, you can click the adjacent ellipsis (**…**) button to display the **Configure Pipeline** dialog box, where you configure per-instance pipeline properties for this specific port. Click **Help** in the dialog box for configuration instructions.                                             |
   | **Receive pipeline** | From the drop-down list, select the pipeline that processes messages received through this port. Responses to messages received through this pipeline will also be sent through this pipeline. After you select the pipeline, you can click the adjacent ellipsis (**…**) button to display the **Configure Pipeline** dialog box, where you configure per-instance pipeline properties for this specific port. This property is visible only for Solicit-Response ports. |


5. If you are creating a solicit-response send port, in the left pane, click **Inbound Maps** and do the following, repeating as necessary if you want to add multiple maps:  


   |      Use this       |                                                                             To do this                                                                              |
   |---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Source Document** | From the drop-down list, select the source document for the inbound map. A send port may have more than one map, but each map should have a unique source document. |
   |       **Map**       |                                     From the drop-down list, select the map to associate with the source and target documents.                                      |
   | **Target Document** |                                              From the drop-down list, select the target document for the inbound map.                                               |


6. In the left pane, click **Outbound Maps** and do the following, repeating as necessary if you want to add multiple maps:  


   |      Use this       |                                         To do this                                         |
   |---------------------|--------------------------------------------------------------------------------------------|
   | **Source Document** |         From the drop-down list, select the source document for the outbound map.          |
   |       **Map**       | From the drop-down list, select the map to associate with the source and target documents. |
   | **Target Document** |         From the drop-down list, select the target document for the outbound map.          |


7. When finished configuring the send port, click **OK**.  

## See Also  
 [Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md)   
 [Managing Pipelines](../core/managing-pipelines.md)   
 [Managing Maps](../core/managing-maps.md)