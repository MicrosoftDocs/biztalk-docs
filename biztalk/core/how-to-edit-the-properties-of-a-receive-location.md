---
title: "How to Edit the Properties of a Receive Location | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [receive locations], properties"
  - "managing [receive locations], editing"
  - "receive locations, properties"
  - "receive locations, editing"
  - "editing, receive locations"
  - "editing, properties"
ms.assetid: 2b622050-a875-4896-bed6-65ca39a26dd3
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Edit the Properties of a Receive Location
This topic describes how to use the BizTalk Server Administration console to edit properties of an existing receive location. For instructions on creating a receive location, see [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To edit the properties of a receive location  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application for which you want to edit the properties of a receive location and then click **Receive Locations**.  
  
3. In the right pane, right-click the receive location, and then click **Properties**.  
  
4. In the **Receive Location Properties** window, edit one or more of the following properties, and then click **OK**:  
  
   |Use this|To do this|  
   |--------------|----------------|  
   |**Name**|Type the name of the receive location.|  
   |**Type**|From the drop-down list, select the transport type, or transport protocol. If you change the transport type, you must configure transport properties, as described next.|  
   |**Configure**|After you select the transport type, click **Configure** to display the **Transport Properties** dialog box and configure adapter properties for the receive location. For instructions, click **Help** in the dialog box. For details on configuring each type of adapter, see the appropriate topic under [Using Adapters](../core/using-adapters.md).|  
   |**Receive handler**|From the drop-down list, select the instance of the BizTalk Server host on which the receive location will run. The receive handler must be running on this host.|  
   |**Receive pipeline**|From the drop-down list, select the receive pipeline to use to receive messages at this receive location.|  
   |**Send pipeline**|From the drop-down list, select the send pipeline to use to send responses from this receive location. This list is available only for a receive location associated with a request-response receive port.|  
   |**Make this the primary location**|Select this check box if you have more than one receive location for a receive port and you want this receive location to represent the receive port when the port needs to be passed to another entity, such as a business partner, that needs to send messages to your organization. The first receive location created is automatically selected as the primary receive location. This property remains selected and unavailable until you designate a different receive location as the primary.|  
  
> [!NOTE]
>  In case you change or modify Receive location, restart the Isolated Host Worker Processes corresponding to the modified receive location.  
  
## See Also  
 [Managing Receive Locations](../core/managing-receive-locations.md)