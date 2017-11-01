---
title: "Remote Environment Node1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15240"
ms.assetid: 661f39ae-b273-458a-ae2a-3e7e591d2ed3
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
robots: noindex,nofollow
---
# Remote Environment Node
Use the ***remote environment*** node to view and manage a remote environment.  
  
 Double-click the ***remote environment*** node to expand the node. The right pane displays the following information about the remote environment selected in the left pane:  
  
-   **Component**. The name of the component.  
  
-   **Type**.  
  
-   **Comment**. Additional information about the remote environment.  
  
> [!IMPORTANT]
>  If you view the list in the right pane of TI Manager and change the order of the columns using the **Add/Remove Columns** command on the shortcut menu, the order of the column headings might not be correct after you close and re-open TI Manager. The next time you open TI Manager, the values in the columns are displayed in the new order you set, but the column headings are in the their default order.  
  
 If you observe that the column headings are no longer in the order you set:  
  
1.  Right-click the node, point to **View**, and then click **Add/Remove Columns**.  
  
2.  On the **Add/Remove Columns** dialog box, click **Restore Defaults**.  
  
3.  Click a different node, then click the node you were just working on.  
  
    > [!NOTE]
    >  The columns should now be in their original order.  
  
 Right-click the ***remote environment*** node to display the following nine options:  
  
-   **Activate**.  
  
-   **Deactivate**.  
  
-   **View**. Displays the following menu items:  
  
    -   **Add/Remove Columns**. Allows you to choose the properties that are displayed in the list view. You can display each property as a separate column in the right pane.  
  
    -   **Large Icons**. Displays large icons for items in the right pane.  
  
    -   **Small Icons**. Displays small icons for items in the right pane.  
  
    -   **List**. Displays only the small icons and the names of the nodes in the right pane.  
  
    -   **Detail**. Displays the small icons and the properties of the nodes in the right pane.  
  
    -   **Customize**. Allows you to change the options to show or hide items displayed in the right pane.  
  
-   **Delete**. Deletes the remote environments selected in the ***remote environments*** node. The deleted item is removed from the ***remote environments*** node and from the administrative data store. If an RE is deleted while it still has objects assigned to it, the objects become unassigned.  
  
-   **Rename**. Renames the selected remote environment. The new name is reflected across all the elements of the WIP console.  
  
-   **Refresh**. Redraws the screen to show any updates.  
  
-   **Export List**. Allows you to save the list of remote environments as a separate text or Unicode text file.  
  
-   **Properties**. Displays the ***remote environment* Properties** dialog box and several tabbed property pages:  
  
    -   **General**  
  
    -   **TCP/IP**  
  
    -   **LU 6.2**  
  
    -   **MQ Series**  
  
    -   **Target**  
  
    -   **Recording**  
  
    -   **Locale**  
  
    -   **Security**  
  
    -   **CICS**  
  
    -   **IMS**  
  
     Use these property pages to view or change the properties of the remote environment.  
  
-   **Help**. Displays a Help topic (this topic) that explains the items that appear in the TI Manager console and the actions you can take.  
  
## See Also  
 [General Tab (Remote Environment Properties)](../core/general-tab-remote-environment-properties.md)   
 [TCP/IP Tab (Remote Environment Properties)](../core/tcp-ip-tab-remote-environment-properties.md)   
 [LU6.2 Tab (Remote Environment Properties)](../core/lu6-2-tab-remote-environment-properties.md)   
 [Target Tab (Remote Environment Properties)](../core/target-tab-remote-environment-properties.md)   
 [Recording Tab (Remote Environment Properties)](../core/recording-tab-remote-environment-properties.md)   
 [Locale Tab (Remote Environment Properties)](../core/locale-tab-remote-environment-properties.md)   
 [Security Tab for SNA (Remote Environment Properties)](../core/security-tab-for-sna-remote-environment-properties.md)   
 [TI Manager Nodes](../core/ti-manager-nodes.md)