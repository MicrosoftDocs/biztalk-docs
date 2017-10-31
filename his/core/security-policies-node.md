---
title: "Security Policies Node2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15375"
ms.assetid: 42697439-e897-4884-b3b9-4acaad46c681
caps.latest.revision: 3
robots: noindex,nofollow
---
# Security Policies Node
Use the **Security Policies** node to view and manage security policies. Security policies define how Windows security credentials are established before the server object is run. The security credentials can be based on the user IDs and passwords delivered to HIP by either the client application program or ENTSSO.  
  
 Double-click the **Security Policies** node to expand the node. The right pane displays the following information about the node:  
  
-   **Security Policy**. The name of the security policy.  
  
-   **Credentials Source**.Indicates whether the credentials used are host-based or application-based.  
  
-   **Group Application**.  
  
> [!IMPORTANT]
>  If you view the list in the right pane of TI Manager and change the order of the columns using the **Add/Remove Columns** command on the shortcut menu, the order of the column headings might not be correct after you close and re-open TI Manager. The next time you open TI Manager, the values in the columns are displayed in the new order you set, but the column headings are in the their default order.  
  
 If you observe that the column headings are no longer in the order you set:  
  
1.  Right-click the node, point to **View**, and then click **Add/Remove Columns**.  
  
2.  On the **Add/Remove Columns** dialog box, click **Restore Defaults**.  
  
3.  Click a different node, then click the node you were just working on.  
  
> [!NOTE]
>  The columns should now be in their original order.  
  
 Right-click the **Security Policies** node to display the following five options:  
  
-   **New**.Displays the following menu item:  
  
    -   **Security Policy**. Launches the **Security Policy Wizard**.  
  
-   **View**. Displays the following menu items:  
  
    -   **Add/Remove Columns**. Allows you to choose the properties that are displayed in the list view. You can display each property as a separate column in the right pane.  
  
    -   **Large Icons**. Displays large icons for items in the right pane.  
  
    -   **Small Icons**. Displays small icons for items in the right pane.  
  
    -   **List**. Displays only the small icons and the names of the nodes in the right pane.  
  
    -   **Detail**. Displays the small icons and the properties of the nodes in the right pane.  
  
    -   **Customize**. Allows you to change the options to show or hide items displayed in the right pane.  
  
-   **Refresh**. Redraws the screen to show any updates.  
  
-   **Export List**. Allows you to save the list of security policies as a separate text or Unicode text file.  
  
-   **Help**. Displays a Help topic (this topic) that explains the items that appear in the TI Manager console and the actions you can take.  
  
## See Also  
 [New Security Policy Wizard](../core/new-security-policy-wizard.md)   
 [Security Policy Node](../core/security-policy-node.md)   
 [TI Manager Nodes](../core/ti-manager-nodes.md)