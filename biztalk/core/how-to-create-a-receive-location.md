---
title: "How to Create a Receive Location | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.procedure.createreceivelocation"
helpviewer_keywords: 
  - "receive locations, creating"
  - "managing [receive locations], creating"
  - "creating, receive locations"
ms.assetid: ec0202cf-0e69-4ae2-aba6-8cd2c3c77e82
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create a Receive Location
This topic describes how to use the BizTalk Server Administration console to create a new receive location and specify the receive port to which it belongs. A receive location is an address where inbound messages arrive as well as the messaging pipeline that processes messages received at that address.  
  
 Before you can create a receive location, a receive port must already exist in this application that of the same type as the receive location you want to create. For instructions on creating a receive port, see [How to Create a Receive Port](../core/how-to-create-a-receive-port.md).  
  
 You can create the following types of receive locations:  
  
-   One-way — used for applications that drop off a message and do not wait synchronously for a reply  
  
-   Request-response — used with applications that require a response to a message  
  
> [!NOTE]
>  The application developer can create a receive location during the development process by using the procedure in this topic.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md). In addition, you need to have appropriate permissions on the SSO database.  
  
### To create a receive location  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application for which you want to create a receive location.  
  
3. Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location** or **Request Response Receive Location**, according to the type of receive location to create.  
  
4. In the Select a Receive Port window, click the receive port that will contain this receive location, and then click **OK**.  
  
5. In the **Receive Location Properties** window, do the following, and then click **OK**:  
  
   |Use this|To do this|  
   |--------------|----------------|  
   |**Name**|Type the name of the receive location.|  
   |**Type**|From the drop-down list, select the transport type, or transport protocol. If you change the transport type, you must configure transport properties, as described next.|  
   |**Configure**|After you select the transport type, click **Configure** to display the **Transport Properties** dialog box and configure adapter properties for the receive location. For instructions, click **Help** in the dialog box. For details on configuring each type of adapter, see the appropriate topic under [Using Adapters](../core/using-adapters.md).|  
   |**Receive handler**|From the drop-down list, select the instance of the BizTalk Server host on which the receive location will run. The receive handler must be running on this host.|  
   |**Receive pipeline**|From the drop-down list, select the receive pipeline to use to receive messages at this receive location.|  
   |**Send pipeline**|From the drop-down list, select the send pipeline to use to send responses from this receive location. This list is available only for a receive location associated with a request-response receive port.|  
   |**Make this the primary location**|Select this check box if you have more than one receive location for a receive port and you want this receive location to represent the receive port when the port needs to be passed to another entity, such as a business partner, that needs to send messages to your organization. The first receive location created is automatically selected as the primary receive location. This property remains selected and unavailable until you designate a different receive location as the primary.|  
  
## See Also  
 [Managing Receive Locations](../core/managing-receive-locations.md)