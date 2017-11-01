---
title: "Computer Node1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15342"
ms.assetid: 989a6380-3db2-4020-bec4-4d05761e47d0
caps.latest.revision: 3
robots: noindex,nofollow
---
# Computer Node
Use the **Computer** node to view and manage the applications running on the computer that is selected in the left pane. An application represents the execution environment for Windows server objects that are initiated by, or driven from, requests from the host computer.  
  
 Double-click the **Computer** node to expand the **Computer** node. The right pane displays the following information about the application:  
  
-   **Application**. Displays the name of the application.  
  
-   **PID**. Displays the process ID of the HIPService. **0** indicates that HIPService is not running.  
  
-   **Thread Count**. Displays the minimum number of worker threads the runtime always has active.  
  
-   **Maximum Queue Depth**. Displays the maximum number of requests that are stored in the queue waiting to be processed before new requests are rejected.  
  
-   **Comment**. Displays additional information about the application.  
  
> [!IMPORTANT]
>  If you view the list in the right pane of TI Manager and change the order of the columns using the **Add/Remove Columns** command on the shortcut menu, the order of the column headings might not be correct after you close and re-open TI Manager. The next time you open TI Manager, the values in the columns are displayed in the new order you set, but the column headings are in the their default order.  
  
 If you observe that the column headings are no longer in the order you set:  
  
1.  Right-click the node, point to **View**, and then click **Add/Remove Columns**.  
  
2.  On the **Add/Remove Columns** dialog box, click **Restore Defaults**.  
  
3.  Click a different node, then click the node you were just working on.  
  
     The columns should now be in their original order.  
  
 Right-click the **Computer** node to display the following five options:  
  
-   **New**.Displays the following menu items:  
  
    -   **Empty Application**. Launches the **New Application** dialog box, which allows you to define an application that does not have executable objects associated with it.  
  
    -   **Configured Application**. Launches the **New Application Deployment Wizard**, which walks you through the steps of creating the application, local environment, host environment, and objects.  
  
-   **View**. Displays the following menu items:  
  
    -   **Add/Remove Columns**. Allows you to choose the properties that are displayed in the list view. You can display each property as a separate column in the right pane.  
  
    -   **Large Icons**. Displays large icons for items in the right pane.  
  
    -   **Small Icons**. Displays small icons for items in the right pane.  
  
    -   **List**. Displays only the small icons and the names of the nodes in the right pane.  
  
    -   **Detail**. Displays the small icons and the properties of the nodes in the right pane.  
  
    -   **Customize**. Allows you to change the options to show or hide items displayed in the right pane.  
  
-   **Refresh**. Redraws the screen to show any updates.  
  
-   **Export List**. Allows you to save the list of applications as a separate text or Unicode text file.  
  
-   **Help**. Displays a Help topic (this topic) that explains the items that appear in the TI Manager console and the actions you can take.  
  
## See Also  
 [Application](../core/application.md)   
 [TI Manager Nodes](../core/ti-manager-nodes.md)