---
title: "How to Configure Tracking for a Receive Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [receive ports], configuring"
  - "configuring [HAT tracking], receive ports"
  - "tracking, receive ports"
  - "receive ports, tracking"
  - "configuring, tracking"
  - "receive ports, configuring"
  - "tracking, configuring"
  - "HAT, receive ports"
  - "configuring, receive ports"
  - "managing [receive ports], tracking"
ms.assetid: dd569e84-cb1c-4191-912a-0c2eb2781a85
caps.latest.revision: 25
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Tracking for a Receive Port
This topic describes how to use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to configure tracking for a receive port, such as options to view message bodies and promoted properties.. This helps you monitor the health of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] implementation and identify any bottlenecks. The tracking settings that you configure apply to all of the instances of the receive port.  
  
 For more information about the message event and service instance tracking features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Checklist: Message and Instance Data Tracking](../core/checklist-message-and-instance-data-tracking.md)  
  
 The tracking settings that you configure apply to all of the instances of the receive port.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group. For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To configure tracking for a receive port  
  
1. Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure tracking for a receive port.  
  
3. Click **Receive Ports**, right-click the receive port and click **Tracking**.  
  
   > [!NOTE]
   >  Before enabling the message body tracking on a receive port, ensure if you want to track the receive port at all; it could be an overhead. For example, a receive pipeline RcvPipe is used at several receive locations in different receive ports. If you enable the message body tracking option on RcvPipe, it leads to message body tracking on all the receive locations, which you might not want to do. Hence, set the message body tracking on receive ports as per your requirement.  
  
4. Configure the tracking options you want, as described in the following table, and then click **OK**.  
  
   |Use this|To do this|  
   |--------------|----------------|  
   |**Track Message Bodies - Request message before port processing**|Select this check box to save and track message content before the message is received.|  
   |**Track Message Bodies - Request message after port processing**|Select this check box to save and track message content after the message is received.|  
   |||  
   |||  
   |**Track Message Properties - Request message before port processing**|Select this check box to track the promoted properties of an inbound message.|  
   |**Track Message Properties - Request message after port processing**|Select this check box if you want to track the promoted properties of an outbound message.|  
   |||  
   |||  
  
## See Also  
 [Managing Receive Ports](../core/managing-receive-ports.md)