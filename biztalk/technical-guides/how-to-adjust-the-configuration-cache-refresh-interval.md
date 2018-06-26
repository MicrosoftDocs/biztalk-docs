---
title: "How to Adjust the Configuration Cache Refresh Interval | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63c6c998-e9c0-48f1-a36a-f1fcb916321b
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Adjust the Configuration Cache Refresh Interval
The configuration cache refresh interval defines the time period in which BizTalk Server updates the configuration of the endpoints. When you start BizTalk Server, all items in BizTalk Server administration, such as MessageBox databases, server properties, adapters, and connections to the Tracking database, are stored in the configuration cache. All items in the cache are refreshed by the configuration refresh interval. By default this is every 60 seconds, except for the server database connections and server properties. This means that if you change the general properties for a BizTalk group, such as the SMTP host, the changes are picked up within 60 seconds. System changes made outside the currently open instance of the BizTalk Server Administration console are not reflected until you refresh it.  
  
 The configuration cache refresh interval is part of the BizTalk group properties.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group.  
  
### To adjust the cache refresh interval  
  
1. Click **Start**, click **All Programs**, click **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, right-click **BizTalk Group**, and then click **Settings**.  
  
3. In the **BizTalk Settings Dashboard** dialog box, select the **General** tab. For the **Configuration refresh interval** property, type or select the time (in seconds) that all items in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administration cache must wait between configuration cache refreshes, and then click **OK**.  
  
   > [!NOTE]  
   >  Items involved in the refresh include the MessageBox databases, server properties, adapters, and connections to the Tracking database.  
  
   > [!NOTE]  
   >  By default, all objects in the configuration cache are refreshed every 60 seconds, except for the server database connections and server properties.