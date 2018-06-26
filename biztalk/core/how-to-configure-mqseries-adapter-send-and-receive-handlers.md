---
title: "How to Configure MQSeries Adapter Send and Receive Handlers | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "receive handlers, MQSeries adapters"
  - "configuring [MQSeries adapters], receive handlers"
  - "MQSeries adapters, send handlers"
  - "MQSeries adapters, receive handlers"
  - "send handlers, MQSeries adapters"
  - "configuring [MQSeries adapters], send handlers"
ms.assetid: e1cfc415-50d2-440b-9301-ad69da28ad3e
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure MQSeries Adapter Send and Receive Handlers
You can configure some properties for the send and receive handlers for the MQSeries adapter through the BizTalk Server Administration console. The process described in [How to Configure MQSeries Adapter Receive Locations and Send Ports](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md) establishes the values for the majority of send handler properties.  

## To configure the send and receive handlers  
 Follow these steps to configure send and receive handlers for the MSQeries adapter:  

1. Click **Start**, point to **Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  

2. In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, click to expand **Platform Settings**, and then click to expand **Adapters**.  

3. In the expanded adapter list, select **MQSeries**. The list of send and receive handlers that are bound to the MQSeries adapter appear in the right pane.  

4. In the right pane, double-click a send or receive handler in the right pane.  

5. In the **Adapter Handler Properties** dialog box, click **Properties**.  

6. In the **MQSeries Transport Properties** dialog box, do the following:  


   |           Use this            |                                    To do this                                    |
   |-------------------------------|----------------------------------------------------------------------------------|
   | **Maximum Messages in Batch** | Set the maximum number of messages in a batch. Applies only to the send handler. |
   |          **Server**           |      The name of the computer that is running MQSeries Server for Windows.       |


7. Click **OK**.  

   > [!NOTE]
   >  The Receive Location and Send Port properties override the Receive Handler and Send Handler values. If there is no value for the Receive Location or Send Port properties, the adapter uses the Receive Handler and Send Handler values respectively.  

8. Click **OK**.  

## See Also  
 [How to Configure MQSeries Adapter Receive Locations and Send Ports](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md)   
 [Configuring the MQSeries Adapter](../core/configuring-the-mqseries-adapter.md)