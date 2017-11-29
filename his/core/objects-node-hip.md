---
title: "Objects Node (HIP)1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/17/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15350"
ms.assetid: 4c983c93-fd12-4100-a1a8-e998c9a059c4
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
robots: noindex,nofollow
---
# Objects Node (HIP)
Use the **Objects** node to view and manage COM and .NET Framework objects accessible from a host. Objects contain the metadata definitions for the server objects created as TI Projects in Visual Studio.  
  
 Double-click the **Objects** node to expand the node. The right pane displays the following information about the node:  
  
-   **Object**. The name of the object entry. The default name is the ProgID (for COM) or Namespace.Interface (for .NET), but you can change the name on the *object* context menu.  
  
-   **Type**. The type of object.  
  
-   **Component**. The programming identifier of the COM object or the interface name of the .Net object.  
  
-   **Method Count**. The number of methods on the object.  
  
-   **Comment**. Additional information about the object.  
  
    > [!IMPORTANT]
    >  If you view the list in the right pane of TI Manager and change the order of the columns using the **Add/Remove Columns** command on the shortcut menu, the order of the column headings might not be correct after you close and re-open TI Manager. The next time you open TI Manager, the values in the columns are displayed in the new order you set, but the column headings are in the their default order.  
  
 If you observe that the column headings are no longer in the order you set:  
  
1.  Right-click the node, point to **View**, and then click **Add/Remove Columns**.  
  
2.  On the **Add/Remove Columns** dialog box, click **Restore Defaults**.  
  
3.  Click a different node, then click the node you were just working on.  
  
    > [!NOTE]
    >  The columns should now be in their original order.  
  
 Right-click the **Objects** node to display the following five options:  
  
-   **New**.Displays the following menu item:  
  
    -   **Object**. Launches the **HIP Object Wizard**.  
  
-   **View**. Displays the following menu items:  
  
    -   **Add/Remove Columns**. Allows you to choose the properties that are displayed in the list view. You can display each property as a separate column in the right pane.  
  
    -   **Large Icons**. Displays large icons for items in the right pane.  
  
    -   **Small Icons**. Displays small icons for items in the right pane.  
  
    -   **List**. Displays only the small icons and the names of the nodes in the right pane.  
  
    -   **Detail**. Displays the small icons and the properties of the nodes in the right pane.  
  
    -   **Customize**. Allows you to change the options to show or hide items displayed in the right pane.  
  
-   **Refresh**. Redraws the screen to show any updates.  
  
-   **Export List**. Allows you to save the list of objects as a separate text or Unicode text file.  
  
-   **Help**. Displays a Help topic (this topic) that explains the items that appear in the TI Manager console and the actions you can take.  
  
## See Also  
 [Object Wizard (for HIP)](../core/object-wizard-for-hip.md)   
 [Object Node (HIP)](../core/object-node-hip.md)   
 [TI Manager Nodes](../core/ti-manager-nodes.md)