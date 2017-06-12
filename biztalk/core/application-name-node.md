---
title: "&lt;Application Name&gt; Node | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.node.application"
ms.assetid: b5af7d8a-2bb7-40bb-9c72-e51ea70e2d7b
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# &lt;Application Name&gt; Node
Use the **\<Application Name>** node to view artifacts specific to the application, to start, stop, and configure applications, and to import and export bindings and Microsoft Installer files. Right-click a specific **\<Application Name>** node to display the following commands:  
  
-   **Start**. Displays the **Start '\<Application Name>' Application** dialog box, which enables you to select referenced applications and other application artifacts to start with the current application. If the selected application has not been configured, a message appears that notifies you that the application is not fully configured and offers you the opportunity to configure it.  
  
-   **Stop**. Displays the **Stop '\<Application Name>' Application** dialog box.  
  
-   **Configure**. Displays the **Configure Application** dialog box, which contains specific artifacts that you must configure before the application can start.  
  
-   **Import**. This menu item displays a submenu containing the following commands:  
  
    -   **MSI file**. Displays the Import MSI Wizard, which you can use to import a Microsoft Installer file.  
  
    -   **Bindings**. Displays the **Import Bindings** dialog box, which you use to import a bindings file into the selected application.  
  
-   **Export**. This menu item displays a submenu containing the following commands:  
  
    -   **MSI file**. Displays the Export MSI File Wizard, which you use to export the selected application to a Microsoft Installer file that you specify.  
  
    -   **Policies**. Displays the **Export Policies** dialog box, which you use to export business rules and vocabularies to an *.xml file.  
  
    -   **Bindings**. Displays the **Export Bindings** dialog box, which exports bindings for the selected application to a file.  
  
-   **Add**. This menu item displays a submenu containing the following commands:  
  
    -   **BizTalk Assemblies**. Displays the **Add Resources** dialog box, which you use to add assemblies and other resources to an application.  
  
    -   **PreProcessing Scripts**. Displays the **Add Resources** dialog box, which you use to add pre-processing scripts and other resources to an application.  
  
    -   **PostProcessing Scripts**. Displays the **Add Resources** dialog box, which you use to add post-processing scripts and other resources to an application.  
  
    -   **Resources**. Displays the **Add Resources** dialog box, which you use to bindings, COM objects, and other resources to an application.  
  
    -   **Policies**. Displays the **Add Policy** dialog box, which you use to associate a policy with the current application.  
  
    -   **References**. Displays the **Add Application Reference** dialog box, which you use to add a reference to another application.  
  
-   **Delete**. Deletes the selected application.  
  
-   **Refresh**. Updates the details pane with the latest application configuration and status information.  
  
-   **Properties**. Displays the **Application Properties: \<Application Name> Properties** window.  
  
## See Also  
 [Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md)   
 [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md)   
 [Importing BizTalk Applications, Bindings, and Policies](../core/importing-biztalk-applications-bindings-and-policies.md)   
 [Importing BizTalk Applications, Bindings, and Policies](../core/importing-biztalk-applications-bindings-and-policies.md)   
 [How to Uninstall a BizTalk Application](../core/how-to-uninstall-a-biztalk-application.md)