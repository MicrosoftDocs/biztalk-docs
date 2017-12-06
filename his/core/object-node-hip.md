---
title: "Object Node (HIP)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15349"
ms.assetid: 19ba7513-c8f6-479f-ada9-f7641023b09f
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
robots: noindex,nofollow
---
# Object Node (HIP)
Use the ***object*** node to create and manage object views. An object view is a representation of the server object itself. A view can include one or more methods of an object, and not all methods have to be defined in a view. You can define one or more views for an object, which enables you to restrict the methods of an object to specific endpoints and host environment pairs.  
  
 Double-click the ***object***node to expand the node. The right pane displays the following information about the view selected in the left pane:  
  
-   **View**. The name of the view.  
  
-   **LE Name**. The name of the local environment.  
  
-   **Security Policy**. The name of the security policy.  
  
-   **Method Count**. The number of methods.  
  
-   **HE Count**. The number of host environments.  
  
-   **Comment**. Additional information about the view.  
  
> [!IMPORTANT]
>  If you view the list in the right pane of TI Manager and change the order of the columns using the **Add/Remove Columns** command on the shortcut menu, the order of the column headings might not be correct after you close and re-open TI Manager. The next time you open TI Manager, the values in the columns are displayed in the new order you set, but the column headings are in the their default order.  
  
 If you observe that the column headings are no longer in the order you set:  
  
1.  Right-click the node, point to **View**, and then click **Add/Remove Columns**.  
  
2.  On the **Add/Remove Columns** dialog box, click **Restore Defaults**.  
  
3.  Click a different node, then click the node you were just working on.  
  
    > [!NOTE]
    >  The columns should now be in their original order.  
  
 Right-click the ***object***node to display the following six options:  
  
-   **New**. Displays the following menu item:  
  
    -   **View**. Launches the **New Object View Wizard**.  
  
-   **View**. Displays the following menu items:  
  
    -   **Add/Remove Columns**. Allows you to choose the properties that are displayed in the list view. You can display each property as a separate column in the right pane.  
  
    -   **Large Icons**. Displays large icons for items in the right pane.  
  
    -   **Small Icons**. Displays small icons for items in the right pane.  
  
    -   **List**. Displays only the small icons and the names of the nodes in the right pane.  
  
    -   **Detail**. Displays the small icons and the properties of the nodes in the right pane.  
  
    -   **Customize**. Allows you to change the options to show or hide items displayed in the right pane.  
  
-   **Refresh**. Redraws the screen to show any updates.  
  
-   **Export List**. Allows you to save the list of objects as a separate text or Unicode text file.  
  
-   **Properties**. Displays the ***object* Properties** dialog box and two tabbed property pages:  
  
    -   **General**  
  
    -   **Methods**  
  
     Use these property pages to view or change the properties of the object.  
  
-   **Help**. Displays a Help topic (this topic) that explains the items that appear in the TI Manager console and the actions you can take.  
  
## See Also  
 [General Tab (Object Properties)](../core/general-tab-object-properties.md)   
 [Methods Tab (Object Properties)](../core/methods-tab-object-properties.md)   
 [New Object View Wizard](../core/new-object-view-wizard.md)   
 [TI Manager Nodes](../core/ti-manager-nodes.md)