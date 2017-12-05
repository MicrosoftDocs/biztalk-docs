---
title: "Remote Environments Node1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15238"
ms.assetid: 121151db-8ddb-4ffb-82c8-8dd4751e6eb6
caps.latest.revision: 4
---
# Remote Environments Node
Use the **Remote Environments** node to manager remote environments. A remote environment defines the characteristics of the non-Windows host environment that receives requests from Windows-initiated processing (WIP) components.  
  
 Double-click the **Remote Environments** node to expand the node. The right pane displays the following information about the node:  
  
-   **Remote Environment**. The names of the remote environment.  
  
-   **Type**. The type of remote environment.  
  
-   **Comment**. Additional information about the remote environment.  
  
> [!IMPORTANT]
>  If you view the list in the right pane of TI Manager and change the order of the columns using the **Add/Remove Columns** command on the shortcut menu, the order of the column headings might not be correct after you close and re-open TI Manager. The next time you open TI Manager, the values in the columns are displayed in the new order you set, but the column headings are in the their default order.  
  
 If you observe that the column headings are no longer in the order you set:  
  
1.  Right-click the node, point to **View**, and then click **Add/Remove Columns**.  
  
2.  On the **Add/Remove Columns** dialog box, click **Restore Defaults**.  
  
3.  Click a different node, then click the node you were just working on.  
  
    > [!NOTE]
    >  The columns should now be in their original order.  
  
 Right-click the **Remote Environments** node to display the following five options:  
  
-   **New**. Displays the following menu items:  
  
    -   **Remote Environment**. Launches the **New Remote Environment Wizard**.  
  
    -   **Capture RE**.Launches the **New Remote Environment Wizard** to create a remote environment type that captures responses and saves those responses in a recording file. After being saved, the responses can be played back using the playback remote environment.  
  
    -   **Playback RE**.Launches the **New Remote Environment Wizard** to create a remote environment type that plays back responses stored in a recording file.  
  
-   **View**. Displays the following menu items:  
  
    -   **Add/Remove Columns**. Allows you to choose the properties that are displayed in the list view. You can display each property as a separate column in the right pane.  
  
    -   **Large Icons**. Displays large icons for items in the right pane.  
  
    -   **Small Icons**. Displays small icons for items in the right pane.  
  
    -   **List**. Displays only the small icons and the names of the nodes in the right pane.  
  
    -   **Detail**. Displays the small icons and the properties of the nodes in the right pane.  
  
    -   **Customize**. Allows you to change the options to show or hide items displayed in the right pane.  
  
-   **Refresh**. Redraws the screen to show any updates.  
  
-   **Export List**. Allows you to save the list of remote environments as a separate text or Unicode text file.  
  
-   **Help**. Displays a Help topic (this topic) that explains the items that appear in the TI Manager console and the actions you can take.  
  
## See Also  
 [New Remote Environment Wizard](../core/new-remote-environment-wizard2.md)   
 [Remote Environment Node](../core/remote-environment-node2.md)   
 [TI Manager Nodes](../core/ti-manager-nodes1.md)