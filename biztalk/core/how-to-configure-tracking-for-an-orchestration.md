---
title: "How to Configure Tracking for an Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, tracking"
  - "orchestrations, HAT"
  - "managing [orchestrations], tracking"
  - "configuring [HAT tracking], orchestrations"
  - "tracking, orchestrations"
  - "HAT, orchestrations"
ms.assetid: 8f5ed525-11f8-4bef-95c4-cfe9c971b663
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Tracking for an Orchestration
This topic describes how to use the BizTalk Server Administration console to configure tracking for an orchestration.  
  
 For more information about creating and using queries, see [Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md). For more information about the tracking features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md).  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To configure tracking for an orchestration  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration for which you want to configure tracking.  
  
3. Click **Orchestrations**, right-click the orchestration for which you want to configure tracking, and then click **Properties**.  
  
4. Click the **Tracking** tab, select the tracking options you want, as described in the following table, and then click **OK**.  
  
   |Option|Description|  
   |------------|-----------------|  
   |**Track Events - Orchestration start and end**|Select this check box to track the orchestration instance before and after processing of the entire business process. Orchestration tracking enables you to see the instances in the tracking query result views.|  
   |**Track Events - Message send and receive**|Select this check box to track message send and receive events. This check box is available only if you select the **Orchestration start and end** check box.|  
   |**Track Events - Shape start and end**|Select this check box when you need to debug orchestration instances in the Orchestration Debugger. When this check box is selected, the event list in the Orchestration Debugger is populated. This check box is available only if you select the **Orchestration start and end** check box.|  
   |**Track Message Bodies - Before orchestration processing**|Select this check box to save and track the actual message content prior to processing by the orchestration instance. This check box is available only if you select the **Message send and receive** check box.|  
   |**Track Message Bodies - After orchestration processing**|Select this check box to save and track the actual message content after processing by the orchestration instance. This check box is available only if you select the **Message send and receive** check box.|  
   |**Track Message Properties - Incoming messages**|Select this check box to track the promoted properties of an inbound message.|  
   |**Track Message Properties - Outgoing messages**|Select this check box to track the promoted properties of an outbound message.|  
  
## See Also  
 [Managing Orchestrations](../core/managing-orchestrations.md)