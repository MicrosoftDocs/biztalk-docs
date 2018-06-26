---
title: "Deploying and Exporting an Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4106a0a7-878d-4052-8eca-02d546233048
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Deploying and Exporting an Application
This section contains detailed information about how to perform the steps involved in deploying a BizTalk application. The topics in this section support the following checklists:  
  
- [Checklist: Deploying an Application](../technical-guides/checklist-deploying-an-application.md), which shows how to deploy an application in a development environment, export it into an .msi file, and then import it into a production environment from the .msi file.  
  
- [Checklist: Exporting Bindings from One Application to Another](../technical-guides/checklist-exporting-bindings-from-one-application-to-another.md), which shows how to export bindings from an application into another application in either a development or production environment.  
  
  You can use the following tools to deploy and manage a BizTalk application:  
  
|                             Tool                             |                                                                                                                                                                                                                                                                                                                                                                                                                                 Use                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|--------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            BizTalk Server Administration console             | From this graphical user interface, you can perform all of the deployment and management operations for a BizTalk application, including the following:<br /><br /> -   Starting the Import, Installation, and Export Wizards<br />-   Adding and removing an application's artifacts, and making other modifications to the application<br />-   Generating BizTalk Server .msi files for a BizTalk application<br />-   Installing the application onto a computer from the .msi file or importing the application from the .msi file into another BizTalk group<br />-   Importing the bindings for an application from a binding file<br /><br /> For more information about the administration console, see [Using the BizTalk Server Administration Console](http://go.microsoft.com/fwlink/?LinkID=154689) (<http://go.microsoft.com/fwlink/?LinkID=154689>). |
|                  BTSTask command-line tool                   |                                                                                                                                                                                                                                                                                                  You can perform many application management tasks from the command line. For more information about the command-line tool, see [BTSTask Command Line Reference](http://go.microsoft.com/fwlink/?LinkId=155003) (<http://go.microsoft.com/fwlink/?LinkId=155003>).                                                                                                                                                                                                                                                                                                   |
|              Scripting and programmability APIs              |                                                                                                                                                                                                                                                           You can use Microsoft Windows Management Instrumentation (WMI) or the BizTalk Explorer Object Model to create and run scripts that automate many application management tasks. For more information about scripting, see [WMI Class Reference](http://go.microsoft.com/fwlink/?LinkId=155004) (<http://go.microsoft.com/fwlink/?LinkId=155004>).                                                                                                                                                                                                                                                           |
| [!INCLUDE[btsVStudio2008](../includes/btsvstudio2008-md.md)] |                                                                                                                                                                                                You can create BizTalk assemblies in Visual Studio, use the Deploy command to automatically deploy them into a BizTalk application, and use BizTalk Explorer to configure application artifacts from within Visual Studio. For more information about working within Visual Studio, see [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](http://go.microsoft.com/fwlink/?LinkID=154719) (<http://go.microsoft.com/fwlink/?LinkID=154719>).                                                                                                                                                                                                |
  
## In This Section  
  
-   [Creating an Application](../technical-guides/creating-an-application.md)  
  
-   [Deploying an Assembly](../technical-guides/deploying-an-assembly.md)  
  
-   [Adding Artifacts to an Application](../technical-guides/adding-artifacts-to-an-application.md)  
  
-   [How to Export an Application to an .msi File](../technical-guides/how-to-export-an-application-to-an-msi-file.md)  
  
-   [How to Export Bindings to a Binding File](../technical-guides/how-to-export-bindings-to-a-binding-file.md)  
  
-   [How to Add a Binding File to an Application1](../technical-guides/how-to-add-a-binding-file-to-an-application1.md)  
  
-   [How to Import an Application from an .msi File](../technical-guides/how-to-import-an-application-from-an-msi-file.md)  
  
-   [How to Install an Application](../technical-guides/how-to-install-an-application.md)  
  
-   [How to Import Bindings from a Binding File](../technical-guides/how-to-import-bindings-from-a-binding-file.md)  
  
-   [Testing an Application](../technical-guides/testing-an-application.md)  
  
-   [How to Add a Reference to an Application](../technical-guides/how-to-add-a-reference-to-an-application.md)