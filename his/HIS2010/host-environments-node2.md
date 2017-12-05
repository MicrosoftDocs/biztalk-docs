---
title: "Host Environments Node2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15347"
ms.assetid: 472fceab-9cc5-44d7-a6ab-f152484a8379
caps.latest.revision: 5
---
# Host Environments Node
Use the **Host Environments** node to manage host environments. The host environment defines which host environments can contact the HIP runtime.  
  
 Double-click the **Host Environments** node to expand the node. The right pane displays the following information about the node:  
  
-   **Host Environment**.The names of the host environments.  
  
-   **Type**. The type of network used to communicate with the host environment (either TCP/IP or SNA).  
  
-   **Data Conversion**. The data conversion routine used.  
  
-   **Send Time-out**. The number of seconds the servicing HIP application waits before it terminates the request if the expected data is not received.  
  
-   **Receive Time-out**. The number of seconds the servicing HIP application waits before it terminates the receive function if the expected data is not received.  
  
-   **Code Page**. The number of the code page used to transform the incoming and outgoing data to a form that can be used by the host application program to represent the character data.  
  
-   **Remote Endpoint Manager**. The IP address of the host or the host name registered in the DNS (for a TCP/IP network); the LU name associated with the host system (for an SNA network).  
  
-   **Comment**. Additional information about the host environment.  
  
> [!IMPORTANT]
>  If you view the list in the right pane of TI Manager and change the order of the columns using the **Add/Remove Columns** command on the shortcut menu, the order of the column headings might not be correct after you close and re-open TI Manager. The next time you open TI Manager, the values in the columns are displayed in the new order you set, but the column headings are in the their default order.  
  
 If you observe that the column headings are no longer in the order you set:  
  
1.  Right-click the node, point to **View**, and then click **Add/Remove Columns**.  
  
2.  On the **Add/Remove Columns** dialog box, click **Restore Defaults**.  
  
3.  Click a different node, then click the node you were just working on.  
  
> [!NOTE]
>  The columns should now be in their original order.  
  
 Right-click the **Host Environments** node to view the following five options:  
  
-   **New**.Displays the following menu item:  
  
    -   **Host environment**. Launches the **New Host Environment Wizard**.  
  
-   **View**. Displays the following menu items:  
  
    -   **Add/Remove Columns**. Allows you to choose the properties that are displayed in the list view. You can display each property as a separate column in the right pane.  
  
    -   **Large Icons**. Displays large icons for items in the right pane.  
  
    -   **Small Icons**. Displays small icons for items in the right pane.  
  
    -   **List**. Displays only the small icons and the names of the nodes in the right pane.  
  
    -   **Detail**. Displays the small icons and the properties of the nodes in the right pane.  
  
    -   **Customize**. Allows you to change the options to show or hide items displayed in the right pane.  
  
-   **Refresh**. Redraws the screen to show any updates.  
  
-   **Export List**. Allows you to save the list of host environments as a separate text or Unicode text file.  
  
-   **Help**. Displays a Help topic (this topic) that explains the items that appear in the TI Manager console and the actions you can take.  
  
## See Also  
 [New Host Environment Wizard](../HIS2010/new-host-environment-wizard1.md)   
 [TI Manager Nodes](../HIS2010/ti-manager-nodes1.md)