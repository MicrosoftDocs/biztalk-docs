---
title: "How to Set an Alert | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "alerts, creating"
  - "Query Builder [BAM portal], creating alerts"
  - "queries [BAM], aggregations"
  - "Query Builder [BAM portal], activity searches"
  - "Query Builder [BAM portal], aggregation alerts"
  - "queries [BAM], alerts"
  - "aggregations, alerts"
ms.assetid: 8745d2c6-5bc0-4d7a-8c17-361535f5c6e6
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Set an Alert
You can set an alert by attaching it to an activity search or drilling down through an aggregation.  
  
> [!NOTE]
>  Before setting an alert on a query, you should run the query and evaluate whether the alert cycle durations are appropriate for the process you are monitoring. If the cycle duration is too short, it is possible for an alert condition to occur in a transient manner and thus be missed by the alerting system.  
  
> [!NOTE]
>  If you click the back button during these procedures, you may receive the following message: "Warning: page has expired." To return to the previous content, press F5. (You may have to press F5 several times.)  
  
> [!NOTE]
>  When you create the first alert on a view, there will be no data displayed for the alert. Defining an alert does not collect alert data from the time frame before the alert was created.  
  
## Prerequisites  
 The following are prerequisites for performing the procedures in this topic:  
  
-   You must have a deployed view.  
  
-   You must have an activity search for an instance alert.  
  
-   You must have a populated aggregation for an aggregation alert.  
  
### To set an alert on an activity search  
  
1.  In the **My Views** frame, click a view to expand the list of tasks for the view.  
  
2.  Click the **Activity Search** task under the view you expanded.  
  
3.  Create or open an activity search. For information about how to do this, see [How to Create a Query in Activity Search](../core/how-to-create-a-query-in-activity-search.md).  
  
4.  In the content frame of the BAM portal, click the **Set Alert** button. The content frame will load with the alert creation template.  
  
5.  In the **Name** text box, type a descriptive name for the alert.  
  
    > [!NOTE]
    >  Names are limited to 100 characters and cannot contain the following characters: ~!@#$%^&amp;*();  If you enter any of these characters in a name, a dashed red border appears around the text field indicating an error that you must correct to complete the action.  
  
6.  If you do not want the alert enabled at this time, clear the **Alert Enabled** check box.  
  
7.  In the **Message** text box, type the message that is delivered when the alert is triggered.  
  
8.  From the **Priority** drop-down list, choose the priority level for this alert. The priority setting indicates the severity of the issue on which the alert was set.  
  
9. In the **Owners** text box, type the aliases of the owners of this alert. Use semicolons between the names of multiple users.  
  
10. In the **Alert Security** area, select the check box to allow other users to see this alert and subscribe to it.  
  
    > [!NOTE]
    >  You can switch the alert security between private and public at any time; the presence of subscribers to the alert does not affect this action. When you switch the alert security from public to private, however, you should consider whether there are any subscribers to the alert. If there are subscribers to the alert, they will have no way to edit their subscription when the alert is made private.  
  
11. In the upper-right corner of the **Alert Details** area, click the **Save Alert** button.  
  
### To set an alert on an aggregation  
  
1.  In the **My Views** frame, click a view to expand the list of tasks for the view.  
  
2.  Click the **Aggregations** task in **My Views** under the view you expanded.  
  
3.  In the content frame of the BAM portal, right-click a cell in the totals column of the PivotTable report. This opens a context menu with functions that are available to perform on the aggregation total.  
  
    > [!NOTE]
    >  You can set an alert on a specific component of the aggregation total by expanding that line item. You can expand succeeding levels in this manner until you reach the level at which you want to set your alert.  
  
4.  At the top of the context menu, click **Create Alert**. The content frame will load with the alert creation template.  
  
5.  In the **Name** text box, type a descriptive name for the alert.  
  
    > [!NOTE]
    >  Names are limited to 100 characters and cannot contain the following characters: ~!@#$%^&amp;*();  If you enter any of these characters in a name, a dashed red border appears around the text field indicating an error that you must correct to complete the action.  
  
6.  If you do not want the alert enabled at this time, clear the **Alert Enabled** check box.  
  
7.  In the **Message** text box, type the message that is delivered when the alert is triggered.  
  
8.  From the **Priority** drop-down list, choose the priority level for this alert. The priority setting indicates the severity of the issue on which the alert was set.  
  
9. In the **Owners** text box, type the aliases of the owners of this alert. Use semicolons between the names of multiple users.  
  
10. In the **Threshold** area, select a comparison condition from the **Count** drop-down list.  
  
11. In the **Duration** text box, enter the number of time units across which the threshold is measured.  
  
12. From the **Duration** drop-down list, select the unit of time.  
  
13. In the **Alert Security** area, select the check box to allow other users to see this alert and subscribe to it.  
  
    > [!NOTE]
    >  You can switch the alert security between private and public at any time; the presence of subscribers to the alert does not affect this action. When you switch the alert security from public to private, however, you should consider whether there are any subscribers to the alert. If there are subscribers to the alert, they will have no way to edit their subscription when the alert is made private.  
  
14. In the upper-right corner of the **Alert Details** area, click the **Save Alert** button.  
  
## See Also  
 [How to Create a Query in Activity Search](../core/how-to-create-a-query-in-activity-search.md)