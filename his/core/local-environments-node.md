---
title: "Local Environments Node1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/19/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15345"
ms.assetid: c90d3c9f-78bc-4f04-b41f-a58c806a253d
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
robots: noindex,nofollow
---
# Local Environments Node
Use the **Local Environments** node to manage local environments. A local environment defines how a remote environment contacts the host-initiated processing (HIP) runtime.  
  
 Double-click the **Local Environments** node to expand the node. The right pane displays the following information about the local environments:  
  
-   **Local Environment**. The name of the local environment.  
  
-   **Type**. The type of network used to communicate with the host environment (either TCP/IP or SNA).  
  
-   **Transport Class**. The class of the transport object.  
  
-   **Endpoint Manager**. The IP address of the local host (for a TCP/IP network); the name of the LU alias (for an SNA network).  
  
-   **Endpoints**. The endpoints used to communicate with the host.  
  
-   **Comment**. Additional information about the local environment.  
  
> [!IMPORTANT]
>  If you view the list in the right pane of TI Manager and change the order of the columns using the **Add/Remove Columns** command on the shortcut menu, the order of the column headings might not be correct after you close and re-open TI Manager. The next time you open TI Manager, the values in the columns are displayed in the new order you set, but the column headings are in the their default order.  
  
> [!NOTE]
>  If you observe that the column headings are no longer in the order you set:  
  
1.  Right-click the node, point to **View**, and then click **Add/Remove Columns**.  
  
2.  On the **Add/Remove Columns** dialog box, click **Restore Defaults**.  
  
3.  Click a different node, then click the node you were just working on.  
  
> [!NOTE]
>  The columns should now be in their original order.  
  
 Right-click the **Local Environments** node to view the following five options:  
  
-   **New**.Displays the following menu items:  
  
    -   **Local environment**. Launches the **New Local Environment Wizard**.  
  
-   **View**. Displays the following menu item:  
  
    -   **Add/Remove Columns**. Allows you to choose the properties that are displayed in the list view. You can display each property as a separate column in the right pane.  
  
    -   **Large Icons**. Displays large icons for items in the right pane.  
  
    -   **Small Icons**. Displays small icons for items in the right pane.  
  
    -   **List**. Displays only the small icons and the names of the nodes in the right pane.  
  
    -   **Detail**. Displays the small icons and the properties of the nodes in the right pane.  
  
    -   **Customize**. Allows you to change the options to show or hide items displayed in the right pane.  
  
-   **Refresh**. Redraws the screen to show any updates.  
  
-   **Export List**. Allows you to save the list of local environments as a separate text or Unicode text file.  
  
-   **Help**. Displays a Help topic (this topic) that explains the items that appear in the TI Manager console and the actions you can take.  
  
## See Also  
 [New Local Environment Wizard (TI)](../core/new-local-environment-wizard-ti.md)   
 [Local Environment Node](../core/local-environment-node.md)   
 [TI Manager Nodes](../core/ti-manager-nodes.md)