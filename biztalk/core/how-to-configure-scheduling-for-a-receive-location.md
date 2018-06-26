---
title: "How to Configure Scheduling for a Receive Location | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring, receive locations"
  - "managing [receive locations], scheduling"
  - "scheduling, receive locations"
  - "managing [receive locations], configuring"
ms.assetid: 2653e1c3-ddbd-4d3f-be64-2a5fcd7cf267
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Scheduling for a Receive Location
This topic describes how to use the BizTalk Server Administration console to configure scheduling properties for a receive location. You can specify the dates when you want the receive location to start and stop processing messages. You can also specify certain times of the day during which you want the receive location to process messages.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To configure scheduling for a receive location  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure scheduling for a receive location.  
  
3. Click **Receive Locations**, right-click the receive location, and click **Properties**.  
  
4. In the left pane, click **Schedule**, configure scheduling properties as described in the following table, and then click **OK**.  
  
   |Use this|To do this|  
   |--------------|----------------|  
   |**Start date**|Select this check box, and then from the pull-down calendar, select the date on which the receive location starts processing messages. To change the year, click the displayed year.|  
   |**Stop date**|Select this check box, and then from the pull-down calendar, select the date on which the receive location stops processing messages. This property is optional. If you do not specify a stop date, the receive location remains active until it is disabled.|  
   |**Enable service window**|Select this check box to configure the receive location to receive messages only at specified times of the day, then specify the times in the **Start time and Stop time** boxes. If the check box is cleared, the receive location receives messages at any time. The default value is false (cleared).|  
   |**Start time**|Specify the time when the receive location should begin to receive messages. This box is available only when the **Enable service window** check box is selected.|  
   |**Stop time**|Specify the time when the receive location should cease to receive messages. This box is available only when the **Enable service window** check box is selected.|  
  
## See Also  
 [Managing Receive Locations](../core/managing-receive-locations.md)