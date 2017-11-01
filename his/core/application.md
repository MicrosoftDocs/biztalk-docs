---
title: "Application1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/19/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15343"
ms.assetid: dbf2bd73-00bf-4d12-9139-d9cf545895ae
caps.latest.revision: 3
robots: noindex,nofollow
---
# Application
Use the ***application* [*status*]** node to start or stop an application or to manage the listeners for an application. An application represents the execution environment for Windows server objects that are initiated by, or driven from, requests from the host computer. An application can host more than one server object and can have more than one listening endpoint associated with it.  
  
 The term shown in brackets at the end of the node indicates status of the application:  
  
-   **Stopped**. The execution environment and Windows Server service for the application and its objects are inactive.  
  
-   **Incomplete**. The application is missing one or more objects and, therefore, is not available.  
  
-   **Starting**. TI Manager is starting the execution environment and Windows Server service for the application and its objects.  
  
-   **Active**. The execution environment for the application is running and the listeners and local environments are active.  
  
 Double-click the ***applications* [*status*]** node to expand the node. The right pane displays the following information about the listeners:  
  
-   **Listener**.The name of the listener.  
  
-   **Type**. The type of network (either TCP/IP or SNA).  
  
-   **Listening Address**. For a TCP/IP network, the local host. For an SNA network, the local LU defined in the local environment.  
  
-   **Endpoints**. The endpoints used to communicate with the host.  
  
> [!IMPORTANT]
>  If you view the list in the right pane of TI Manager and change the order of the columns using the **Add/Remove Columns** command on the shortcut menu, the order of the column headings might not be correct after you close and re-open TI Manager. The next time you open TI Manager, the values in the columns are displayed in the new order you set, but the column headings are in the their default order.  
  
> [!NOTE]
>  If you observe that the column headings are no longer in the order you set:  
  
1.  Right-click the node, point to **View**, and then click **Add/Remove Columns**.  
  
2.  On the **Add/Remove Columns** dialog box, click **Restore Defaults**.  
  
3.  Click a different node, then click the node you were just working on.  
  
> [!NOTE]
>  The columns should now be in their original order.  
  
 Right-click the **Application** node to view the following 12 options:  
  
-   **Tracing**. Launches the ***application* Trace Options** dialog box. You can select one or more of the following categories for tracing and select one or more options within a category:  
  
    -   **General**. Provides high-level information about the end-to-end application processing.  
  
    -   **Transport**. Provides detailed connection information about the activities on the SNA or TCP network.  
  
    -   **Convert**. Provides detailed information about the data conversion between COM and .NET data on the servers and COBOL or Report Program Generator (RPG) data on the host.  
  
    -   **Read Lib**. Provides information about the contents of the type library; used to augment the information in the **Convert** trace.  
  
    -   **Flow Control Proxy**. Provides detailed information about object instantiation, state transitions, and method invocation.  
  
-   **Reload Definitions**. Performs a dynamic refresh of the application listener's endpoints and resolution tables. An application gets a snapshot of the configuration database at start-up. Any subsequent changes to the configuration do not affect the application until the definitions are reloaded. When you select **Reload Definitions**, the application re-reads all configuration information from the configuration database and applies it immediately. All new requests are processed using the updated resolution information. Working requests that were in progress at the time **Reload Definitions** was clicked are not affected by the update. The resolution information remains unchanged until the work request is completely processed.  
  
-   **Start**. Starts the host-initiated processing (HIP) environment for the selected application. Any listeners available for auto-start, as defined on the application property page of a listener that is associated with the application, are started when the application is started. After the application is started, **Start** is disabled and **Stop** is enabled.  
  
-   **Stop**. Stops the HIP environment for the selected application. All listeners are stopped when the application is stopped. All pending work is halted immediately and all listening activity is terminated immediately. After the application is stopped, **Stop** is disabled and **Start** is enabled.  
  
-   **New**. Displays a list of the following menu items:  
  
    -   **Listener**. Launches the **Local Environment** dialog box for you to define a new listening point.  
  
-   **View**. Displays the following menu items:  
  
    -   **Add/Remove Columns**. Allows you to choose the properties that are displayed in the list view. You can display each property as a separate column in the right pane.  
  
    -   **Large Icons**. Displays large icons for items in the right pane.  
  
    -   **Small Icons**. Displays small icons for items in the right pane.  
  
    -   **List**. Displays only the small icons and the names of the nodes in the right pane.  
  
    -   **Detail**. Displays the small icons and the properties of the nodes in the right pane.  
  
    -   **Customize**. Allows you to change the options to show or hide items displayed in the right pane.  
  
-   **Delete**. Deletes the application from the computer. You can delete an application if it is stopped. The deleted item is removed from the specific computer it was defined on and from the configuration database.  
  
-   **Rename**. Renames the selected application. The new name is reflected across all elements of the HIP console.  
  
-   **Refresh**. Redraws the screen to show any updates.  
  
-   **Export List**. Allows you to save the list of applications as a separate text or Unicode text file.  
  
-   **Properties**. Displays the ***application* Properties** dialog box and three tabbed property pages:  
  
    -   **General**  
  
    -   **Advanced**  
  
    -   **.NET assembly path**  
  
     Use the property pages to view or change the properties of the application.  
  
-   **Help**. Displays a Help topic (this topic) that explains the items that appear in the TI Manager console and the actions you can take.  
  
## See Also  
 [General Tab (Application Properties)](../core/general-tab-application-properties.md)   
 [Advanced Tab (Application Properties)](../core/advanced-tab-application-properties.md)   
 [.NET Assembly Path Tab (Application Properties)](../core/net-assembly-path-tab-application-properties.md)   
 [TI Manager Nodes](../core/ti-manager-nodes.md)