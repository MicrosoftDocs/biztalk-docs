---
title: "How to Import an Application from an .msi File | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5472df9-9f1e-42d5-82e0-cc559caf56b3
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Import an Application from an .msi File
You can use the Import MSI Wizard in the BizTalk Server Administration Console or BTSTask to import a BizTalk application from an .msi file into a BizTalk group in the target environment and install the application on individual host instances in the group. The full import process performs the following operations:  
  
- A group-level deployment of the application  
  
- A server-level installation of the application.  
  
  **Group-Level Application Deployment**  
  
  You perform a group-level deployment of an application on a server in the group by running the Import MIS Wizard from the BizTalk Server Administration console or by running BTSTask. The group-level deployment does the following:  
  
- Creates the application and its artifacts in the group  
  
- Imports bindings resident in the .msi package  
  
- Deploys all BizTalk Server assemblies with their artifacts to the BizTalk Management database for the group  
  
- Runs scripts specified to run at import time.  
  
  If you have added environment-specific binding files to the application, you will have to select the bindings that you want to apply on import.  
  
  **Server-Level Application Installation**  
  
  You perform a server-level installation of an application on each server in a group by double-clicking the .msi file itself, or performing the install process at the end of the Import MSI Wizard. Instead of being done once per group, it is typically done on each BizTalk server that is a member of the group. The server-level installation does the following:  
  
- Installs all BizTalk Server assemblies and dependency assemblies into the global assembly cache of the server, so that this computer has all of the binaries that it needs for runtime  
  
- Rolls out related Web services that might be part of the solution, for example, orchestrations published as Web services.  
  
- Applies computer-specific changes, such as pre-creating MSMQ queues or creating FILE drop folder structures and permissions, which can be done with the help of scripts.  
  
  When you execute an .msi file to install an application, the .msi file creates registration entries in the Add or Remove Programs list, and accelerates deployment by automating deployment of artifacts and their dependencies in the correct order.  
  
  For more information on installing a BizTalk application, see [How to Install an Application](../technical-guides/how-to-install-an-application.md).  
  
  **The Complete Application Deployment and Installation Process**  
  
  The Import MSI Wizard deploys the application on the group. It does not install the application on the individual servers in the group. If the application includes file-based artifacts, you need to install the application on each host instance that will run the assemblies in the application (and any computers running applications that depend on this application). You can do so on the server you ran the Import MSI Wizard on, however, by selecting the **Run the Application Installation Wizard to install the application on the local computer** check box on the Import Succeeded page displayed by the Import MSI Wizard. You can do so on the other servers in the group by double-clicking the .msi file on each of those servers.  
  
  If you are ready to test the application, you can import it into a BizTalk group in a test environment. If your application is ready for staging or production, you can import it into one of those environments.  
  
## Important Considerations  
 When importing a BizTalk application from an .msi file, keep the following in mind:  
  
- **You must specify that you want artifacts to be overwritten in a standard import process.** If you want to overwrite existing artifacts, select the option to overwrite existing artifacts when importing the .msi file.  
  
- **Imported bindings overwrite existing bindings.** When you import an .msi file that contains bindings into an existing application, the existing bindings are overwritten by imported bindings that have the same name. This is the case even when you have not selected the option to overwrite existing artifacts when importing the .msi file. If you do not want the bindings in the application you are exporting to overwrite the bindings in an application into which you are importing the .msi file, then you should not select the binding file as a resource to export during the export operation. For more information about setting the resources for an export, see [How to Export a BizTalk Application](http://go.microsoft.com/fwlink/?LinkID=154848) (http://go.microsoft.com/fwlink/?LinkID=154848).  
  
  As bindings are applied during the import process, bindings that have already been applied are overwritten by new bindings that have the same name. In other words, the last binding of a particular name to be applied takes effect. When you import an application, bindings are applied in the following order:  
  
1.  Application bindings generated by BizTalk Server that were not explicitly added to the application via a binding file, but that were explicitly selected by the user for export into the application .msi file.  
  
2.  Binding files that have been explicitly added, and do not have a target deployment environment specified. Bindings in this set are applied in no specific order.  
  
3.  Bindings that have been explicitly added, and that have an associated target deployment environment that matches the deployment environment selected for application import. Bindings in this set are applied in no specific order.  
  
- **The host specified must exist.** To import an application from an .msi file, a host corresponding to the host specified in the application bindings contained in the .msi file must already exist in the BizTalk group or the import operation will fail. In addition, the host trust level must match.  
  
- **Dependencies can have significant effects upon import operations.** When you import an application that has a dependency on another application, the following rules apply:  
  
  -   If an application that you are importing depends on an artifact in another application, you must add a reference from the first application to the second application. The application and the required artifact must already exist in the destination group. The Import Wizard enables you to add the reference. However, if you are using the ImportApp command of BTSTask, you must add the reference to the application after import. For more information, see [How to Add a Reference to Another Application](http://go.microsoft.com/fwlink/?LinkId=155011) (http://go.microsoft.com/fwlink/?LinkId=155011). The Import Wizard matches the references to existing applications in the group and gives you the option to add a new reference or change an existing reference. While BizTalk Server verifies that the referenced application exists, we recommend that you take the additional step of verifying that the referenced application contains the required artifact.  
  
  -   When you install an application, you must also install any applications on which it depends. When you install an application that has a dependency on an artifact, such as a BizTalk assembly, which is contained in another application, you must first install the application that contains the artifact. For example, if you want to install Application A, and it depends on an assembly in Application B, you must install Application B first. Then you can install Application A. For more information about installing a BizTalk application, see [How to Install an Application](../technical-guides/how-to-install-an-application.md).  
  
  -   If you want to import an application into a different BizTalk group and run it in that group, you must also import any artifacts on which this application depends. You can do this by first importing an application that contains the referenced artifact, or by adding the needed artifact to the application that requires it. For more information about importing a BizTalk application, see [How to Import an Application from an .msi File](../technical-guides/how-to-import-an-application-from-an-msi-file.md).  
  
  For more considerations and information about importing a BizTalk application from an .msi file, see [How to Import a BizTalk Application](http://go.microsoft.com/fwlink/?LinkID=154827) (http://go.microsoft.com/fwlink/?LinkID=154827).  
  
## How to Import an Application  
 For instructions on importing a BizTalk application from an .msi file, see [How to Import a BizTalk Application](http://go.microsoft.com/fwlink/?LinkID=154827) (http://go.microsoft.com/fwlink/?LinkID=154827).