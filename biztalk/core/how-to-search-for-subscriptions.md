---
title: "How to Search for Subscriptions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Query tab [Administration Console], subscriptions"
  - "Query tab [Administration Console], searching"
  - "subscriptions, viewing"
  - "subscriptions, searching"
ms.assetid: 95f8fd20-2750-412b-a67b-18976e7706e2
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Search for Subscriptions
You can use the **Query** tab in the BizTalk Server Administration Console to search for subscriptions. This is useful when you want to review all of the subscriptions defined in the system. When troubleshooting routing failures, you can review subscriptions to see if any of them are improperly configured, thereby causing the routing failure.  

## Prerequisites  
 To perform this procedure, you must be logged on as a member of the BizTalk Server Operators group.  

### To search for subscriptions  

1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].  

2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then click the BizTalk group.  

3. In the details pane, click the **New Query** tab.  

4. In the **Query Expression** group, in the **Value** column, select **Subscriptions** from the drop-down list box.  

5. In the **Field Name** column, in the empty drop-down list box next to the asterisk (**\\***), select one or more of the following:  


   |          Item           |                                    Description                                    |
   |-------------------------|-----------------------------------------------------------------------------------|
   |   **Maximum Matches**   |                         The number of matches to display.                         |
   | **Service Instance ID** |               You can filter subscriptions by service instance ID.                |
   |    **Service Name**     |                   You can filter subscriptions by service name.                   |
   |  **Subscription Type**  | You can filter subscriptions by Activation Subscription or Instance Subscription. |


6. Complete the **Value** column as appropriate for the selection you made in the **Field Name** column.  

7. Continue adding additional lines to the query as appropriate, by completing the **Field Name**, **Operator**, and **Values** columns, and then click **Run Query**.  

## See Also  
 [Using the Administration Console Query Tab](../core/using-the-administration-console-query-tab.md)