---
title: "Applications Node | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.node.applications"
ms.assetid: f8a9f5d3-7745-45a6-af04-caa07e7ba157
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Applications Node
Use the **Applications** node to create new empty applications and to refresh configuration and status information in all applications in the node. The **Applications** node is a container for all applications in the BizTalk group. Right-click the **Applications** node to display the following commands:  
  
-   **Import**. This menu item displays a submenu containing the following commands.  
  
    -   **MSI File**. Displays the Import MSI Wizard, which you use to import a Microsoft Installer package into the Administration Console.  
  
    -   **Policies**. Displays a **Select File** dialog box that you can use to import a business rule set into the Rules database. After you import a policy, you can find it in the **Policies** node under **\<All Artifacts>**. After the policy is published, you can add it to an application.  
  
    -   **Bindings**. Displays the **Import Bindings** dialog box, which you use to import bindings to an assembly.  
  
-   **Export**. This menu item displays a submenu containing the following commands.  
  
    -   **Policies**. Displays the **Export Policies** dialog box, which you use to export a business rule set as an *.xml file.  
  
    -   **Bindings**. Displays the **Export Bindings** dialog box, which you use to export bindings from an assembly that you specify. The dialog box enables you to explicitly pick the level of bindings you want to export.  
  
-   **New**. Displays a submenu containing the following command.  
  
    -   **Application**. Displays the **Application Properties** window, where you create and configure a new empty application within the tree node.  
  
-   **Refresh**. Updates the configuration and status information in the details pane.  
  
## See Also  
 [Importing BizTalk Applications, Bindings, and Policies](../core/importing-biztalk-applications-bindings-and-policies.md)   
 [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md)