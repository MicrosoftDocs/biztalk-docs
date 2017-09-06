---
title: "How to Configure Tracking for a Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring, send ports"
  - "configuring, tracking"
  - "tracking, send ports"
  - "configuring [HAT tracking], send ports"
  - "send ports, tracking"
  - "managing [send ports], configuring"
  - "tracking, configuring"
  - "send ports, configuring"
  - "managing [send ports], tracking"
  - "HAT, send ports"
ms.assetid: f32e97b0-244c-4acc-8f3f-b18cdb9ec0da
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Tracking for a Send Port
This topic describes how to use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to configure tracking for a send port, such as options to view message bodies and promoted properties. This helps you monitor the health of your BizTalk implementation and identify any bottlenecks. The tracking settings that you configure apply to all of the instances of the send port.  
  
 For more information about the message event and service instance tracking features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md)  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group. For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To configure tracking for a send port  
  
1.  Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2.  In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure tracking for a send port.  
  
3.  Click **Send Ports**, right-click the send port, click **Properties**, and then click **Tracking**.  
  
    > [!NOTE]
    >  One send port can be associated with only one send pipeline. If message body tracking is disabled on the send pipeline, nothing can be tracked on the send port as well. In such a scenario, you can disable the "Tracking" options on that send port.  
  
4.  Configure the tracking options you want, as described in the following table, and then click **OK**.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Track Message Bodies - Request message before port processing**|Select this check box to enable you to save and track message content before the message is received. **Note:**  You must enable message body pipeline tracking to successfully track the response message before port processing.|  
    |**Track Message Bodies - Request message after port processing**|Select this check box to enable you to save and track message content after the message is received.|  
    |||  
    |||  
    |**Track Message Properties - Request message before port processing**|Select this check box to track the promoted properties of an inbound message.|  
    |**Track Message Properties - Request message after port processing**|Select this check box if you want to track the promoted properties of an outbound message.|  
    |||  
    |||  
  
## See Also  
 [Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md)