---
title: "How to Create a Receive Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.procedure.createreceiveport"
helpviewer_keywords: 
  - "receive ports, creating"
  - "managing [receive ports], creating"
  - "creating, receive ports"
ms.assetid: 23fae441-be80-4759-b3d6-74787a40e65b
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create a Receive Port
This topic describes how to use the BizTalk Server Administration console to create a receive port. A receive port is a logical grouping of similar receive locations through which services interact with external partners by receiving data.  

 You can create the following types of receive ports:  

- One-way — used for applications that drop off a message and do not wait synchronously for a reply  

- Request-response — used with applications that require a response to a message  

  In addition to the configuration described in this topic, you can also specify tracking options for the messages handled by a receive port, as described in [How to Configure Tracking for a Receive Port](../core/how-to-configure-tracking-for-a-receive-port.md).  

> [!NOTE]
>  If you are creating a receive port on a remote computer and that computer does not have network DTC enabled, you will have to reboot the remote computer after creating the receive port.  

## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  

### To create a receive port  

1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  

2. In the console tree, expand the BizTalk group and the BizTalk application for which you want to create a receive port.  

3. Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port** or **Request Response Receive Port**, according to the type of port you want to create.  

4. In the **Receive Port Properties** window, do the following:  


   |                 Use this                  |                                                                                                                                                                                                                            To do this                                                                                                                                                                                                                             |
   |-------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                 **Name**                  |                                                                                                                                                                                                                    Type the name of the port.                                                                                                                                                                                                                     |
   |           **No authentication**           |                                                                                                                                                                                                 Click this option to disable authentication. This is the default.                                                                                                                                                                                                 |
   | **Drop messages if authentication fails** |                                                                                                                                                                                         Click this option to enable authentication but to drop unauthenticated messages.                                                                                                                                                                                          |
   | **Keep messages if authentication fails** |                                                                                                                                                                                           Click this option to enable authentication and keep unauthenticated messages.                                                                                                                                                                                           |
   |  **Enable routing for failed messages**   | Select this check box to attempt to route any message that fails processing to a subscribing application (such as another receive port or orchestration schedule). Clear the check box to suspend failed messages and generate a negative acknowledgment (NACK). The default value is cleared. For more information, see [How to Enable Routing for Failed Messages for a Receive Port](../core/how-to-enable-routing-for-failed-messages-for-a-receive-port.md). |


5. In the left pane, click **Receive Locations**, and create a new receive location for this receive port. For instructions, see [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).  

6. In the left pane, click **Inbound Maps**, and do the following:  


   |      Use this       |                                  To do this                                   |
   |---------------------|-------------------------------------------------------------------------------|
   | **Source Document** |   From the drop-down list, select the source schema to use with this port.    |
   |       **Map**       | From the drop-down list, select the map you want to associate with this port. |
   | **Target Document** | From the drop-down list, select the destination schema to use with this port. |


7. If you are creating a request-response receive port, then in the left pane, click **Outbound Maps**, and do the following:  


   |      Use this       |                                  To do this                                   |
   |---------------------|-------------------------------------------------------------------------------|
   | **Source Document** |   From the drop-down list, select the source schema to use with this port.    |
   |       **Map**       | From the drop-down list, select the map you want to associate with this port. |
   | **Target Document** | From the drop-down list, select the destination schema to use with this port. |


8. When finished configuring the receive port, click **OK**.  

## See Also  
 [Managing Receive Ports](../core/managing-receive-ports.md)