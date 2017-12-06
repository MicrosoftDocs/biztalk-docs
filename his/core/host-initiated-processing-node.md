---
title: "Host-Initiated Processing Node2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15377"
ms.assetid: 67c1e7b0-9fe6-427c-a5dc-78c600b37053
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
robots: noindex,nofollow
---
# Host-Initiated Processing Node
Use the **Host-Initiated Processing** node to view the major elements used in host-initiated processing (HIP) environment. The major HIP elements are:  
  
-   Computers that have the HIP run-time environment installed. The run-time environment is responsible for accepting incoming requests, instantiating a Microsoft Windows® server object, and returning a reply to the host program that initiated the request.  
  
-   Local environments (LEs) that a HIP runtime uses to listen for incoming requests. The LE definitions contain network-transport specific endpoint identification.  
  
-   Host environments (HEs) that represent the non-Windows host computers or host environments that deliver requests to a HIP run-time environment. The HE is used by the HIP runtime to define the code page and the data conversion object to be used by the HIP runtime when communicating with the host system identified by the HE.  
  
-   Security policies that define how Windows security credentials are established before the server object is invoked.  
  
-   Objects that represent the metadata for the server objects that were created through Microsoft Visual Studio®.  
  
-   Views define the resolution criteria used by TI when directing the call made from a host environment to a server object. Views restrict access to object methods based on the host environment calling the object and the local environment receiving the call.  
  
 Double-click the **Host-Initiated Processing** node to expand the node. The right pane displays the following information about the node:  
  
-   **Name**. The name of the major HIP elements.  
  
 Right-click the **Host-Initiated Processing** node to display the following five options:  
  
-   **View**. Displays the following menu items:  
  
    -   **Add/Remove Columns**. Allows you to choose the properties that are displayed in the list view. You can display each property as a separate column in the right pane.  
  
    -   **Large Icons**. Displays large icons for items in the right pane.  
  
    -   **Small Icons**. Displays small icons for items in the right pane.  
  
    -   **List**. Displays only the small icons and the names of the nodes in the right pane.  
  
    -   **Detail**. Displays the small icons and the properties of the nodes in the right pane.  
  
    -   **Customize**. Allows you to change the options to show or hide items displayed in the right pane.  
  
-   **Refresh**. Redraws the screen to show any updates.  
  
-   **Export List**. Allows you to save the list of elements as a separate text or Unicode text file.  
  
-   **Properties**. Displays the **Host-Initiated Processing Properties** dialog box and one tabbed property page:  
  
    -   **Database**. Displays the name of the database.  
  
-   **Help**. Displays a Help topic (this topic) that explains the items that appear in the TI Manager console and the actions you can take.  
  
## See Also  
 [Computers Node](../core/computers-node.md)   
 [Local Environments Node](../core/local-environments-node.md)   
 [Host Environments Node](../core/host-environments-node.md)   
 [Security Policies Node](../core/security-policies-node.md)   
 [Objects Node (HIP)](../core/objects-node-hip.md)   
 [TI Manager Nodes](../core/ti-manager-nodes.md)