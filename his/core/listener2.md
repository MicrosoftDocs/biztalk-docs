---
title: "Listener2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15364"
ms.assetid: 228d153a-7064-4be5-956f-b2600ac3b205
caps.latest.revision: 3
robots: noindex,nofollow
---
# Listener
Use the ***listener* [*status*]** node to start or stop a listener and to determine what views are associated with the listener.  
  
 The term shown in brackets at the end of the node indicates status of the listener:  
  
-   **Stopped**. The execution environment and Windows Server service for the listener and its views are inactive.  
  
-   **Incomplete**. The listener is missing one or more views or determinants and, therefore, is not available.  
  
-   **Unavailable**. The listener was defined after the application was started.  
  
-   **Starting**. TI Manager is starting the execution environment and Windows Server service for the application and its objects.  
  
-   **Active**. The execution environment for the application is running and the listeners and local environments are active.  
  
 Double-click the ***listener* [*status*]** node to expand the node. The right pane displays the following information about the listener:  
  
-   **View**. The name of the view.  
  
-   **LE Name**. The name of the local environment.  
  
-   **Method Count**. The number of methods.  
  
-   **HE Count**. The number of host environments.  
  
-   **Comment**. Additional information about the listener.  
  
> [!IMPORTANT]
>  If you view the list in the right pane of TI Manager and change the order of the columns using the **Add/Remove Columns** command on the shortcut menu, the order of the column headings might not be correct after you close and re-open TI Manager. The next time you open TI Manager, the values in the columns are displayed in the new order you set, but the column headings are in the their default order.  
  
> [!NOTE]
>  If you observe that the column headings are no longer in the order you set:  
  
1.  Right-click the node, point to **View**, and then click **Add/Remove Columns**.  
  
2.  On the **Add/Remove Columns** dialog box, click **Restore Defaults**.  
  
3.  Click a different node, then click the node you were just working on.  
  
> [!NOTE]
>  The columns should now be in their original order.  
  
 Right-click the ***listener* [*status*]** node to display the following 10 options:  
  
-   **Start**. Starts the host-initiated processing (HIP) service listening on all endpoints defined for the local environment. The HIP application is then ready to receive incoming host requests and to execute methods in accordance with the method resolution criteria. After the listener is started, **Start** is disabled and **Stop** is enabled. After the listener is started, **[started]** appears to the right of the local environment name in the left pane.  
  
-   **Stop**.Stops the HIP service listening on all endpoints defined for the local environment. The HIP application no longer accepts, rejects, services, or queues incoming host requests. After the listener is stopped, **Stop** is disabled and **Start** is enabled. After the listener is stopped, **[stopped]** appears to the right of the local environment name in the left pane.  
  
-   **Pause**. Temporarily suspends the HIP service listening on all endpoints defined for the local environment. The application continues to execute work in progress and work items queued for execution, but it no longer accepts or queues incoming requests. A number of requests are queued internally by the low-level network transport components (for example, for TCP, Windows XP stores up to 5 requests while Microsoft Windows Server stores up to 200 requests by default). After the listener is resumed, the pending requests are delivered to the listener. Depending on the number of the processing queue entries available, some of these requests might be finally rejected by the listener. After the listener is paused, **Pause** is disabled, **Resume** is enabled, and **[paused]** appears to the right of the local environment name in the left pane.  
  
-   **Resume**. Starts the HIP service listening again on all endpoints defined for the local environment. The HIP application is then ready to receive incoming host requests and to execute methods as defined by the method resolution criteria. After the listener resumes, **Resume** is disabled, **Pause** is enabled, and **[started]** appears to the right of the local environment name in the left pane.  
  
-   **View**. Displays the following menu items:  
  
    -   **Add/Remove Columns**. Allows you to choose the properties that are displayed in the list view. You can display each property as a separate column in the right pane.  
  
    -   **Large Icons**. Displays large icons for items in the right pane.  
  
    -   **Small Icons**. Displays small icons for items in the right pane.  
  
    -   **List**. Displays only the small icons and the names of the nodes in the right pane.  
  
    -   **Detail**. Displays the small icons and the properties of the nodes in the right pane.  
  
    -   **Customize**. Allows you to change the options to show or hide items displayed in the right pane.  
  
-   **Delete**. Deletes the application from the computer. You can delete an application if it is stopped. The deleted item is removed from the specific computer it was defined on and from the administrative data store.  
  
-   **Refresh**. Redraws the screen to show any updates.  
  
-   **Export List**. Allows you to save the list of views as a separate text or Unicode text file.  
  
-   **Properties**. Displays the ***listener* Properties** dialog box and three tabbed property pages:  
  
    -   **General**  
  
    -   **Endpoints**  
  
    -   **Application**  
  
> [!NOTE]
>  When viewed from this node, the general and endpoint property pages are read-only. If you want to change a general or endpoint property, right-click the specific ***local environment* Node** under the **Local Environments Node**, and then left-click **Properties** on the shortcut menu.  
  
-   **Help**. Displays a Help topic (this topic) that explains the items that appear in the TI Manager console and the actions you can take.  
  
## See Also  
 [View Node (listener)](../core/view-node-listener-2.md)   
 [General Tab (Listener Properties)](../core/general-tab-listener-properties-2.md)   
 [Endpoints Tab (TCP/IP Listener Properties)](../core/endpoints-tab-tcp-ip-listener-properties-2.md)   
 [Endpoints Tab (SNA Listener Properties)](../core/endpoints-tab-sna-listener-properties-1.md)   
 [Application Tab (Listener Properties)](../core/application-tab-listener-properties-1.md)   
 [TI Manager Nodes](../core/ti-manager-nodes2.md)