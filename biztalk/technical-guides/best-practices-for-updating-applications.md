---
title: "Best Practices for Updating Applications | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 072eaf25-a1ee-4af3-b034-525a04260ef4
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Best Practices for Updating Applications
This topic describes best practices that you should consider using when updating BizTalk applications and artifacts.  
  
## Versioning  
 **Implement a versioning strategy**  
  
- A good versioning strategy is essential if long-running transactions are used or the BizTalk application cannot be taken down to do upgrades or bug fixes. You should plan the versioning strategy of all BizTalk artifacts: schemas, maps, custom adapters, pipelines, pipeline components, orchestrations, business rules, BAM, and custom classes called in orchestrations and maps.  
  
  **Match the assemblies in the BizTalk Management database and the global assembly cache (GAC)**  
  
- Ensure that the same versions of assemblies are in the BizTalk Management database as in the GAC, so that your application functions properly. If you do not always install an assembly in the GAC when you deploy it, you might have different versions in the GAC and the BizTalk Management database, which will cause processing errors during run time.  
  
  **Use the BizTalk Assembly Checker and Remote GAC tool to verify versioning**  
  
- The **BizTalk Assembly Checker and Remote GAC tool** (BTSAssemblyChecker.exe) checks the versions of assemblies deployed to the BizTalk Management database and verifies that they are correctly registered in the GAC on all BizTalk Server computers. You can use this tool to verify that all the assemblies containing the artifacts of a certain BizTalk application are installed on all BizTalk nodes. The tool is particularly useful in conjunction with a solid versioning strategy to verify that the correct version of a set of assemblies is installed on each BizTalk machine, especially when side-by-side deployment approach is used.  
  
- The tool is available with the BizTalk Server installation media at Support\Tools\x86\BTSAssemblyChecker.exe.  
  
  **Use a Versioning Product**  
  
- You should use a versioning product, such as Microsoft Visual Studio® Team Foundation Server 2010, for tracking and versioning BizTalk artifacts. For more information about Microsoft Visual Studio® Team Foundation Server 2010 see [Microsoft Visual Studio® Team Foundation Server 2010](http://go.microsoft.com/fwlink/?LinkId=210637) (http://go.microsoft.com/fwlink/?LinkId=210637)  
  
  **Factor artifacts into multiple BizTalk applications**  
  
- In order to perform assembly versioning of BizTalk artifacts, your BizTalk solution assemblies need to be factored (packaged) in such a way to allow for BizTalk Server versioning. For more information about factoring, see [Adding Artifacts to an Application](../technical-guides/adding-artifacts-to-an-application.md).  
  
## Updating an Application  
 **Use an .msi file to update an application**  
  
-   Upgrading applications is typically a deliberate and precise operation in production. When you upgrade an application, you should normally use a manual checklist. However, you may be able to streamline certain steps by using an .msi file. When you use an .msi file, you can wrap up your application artifacts into a distributable package. An .msi file is particularly useful when you roll out updated DLLs to multiple runtime boxes or perform a group-level deployment. When you create an .msi file, you should exclude all other unchanged resources and bindings from the package.  
  
-   If you update a BizTalk assembly, you should stop, unenlist, re-enlist, and then start BizTalk artifacts manually before and after you import and install the .msi file. For more information about updating a BizTalk assembly, see [Checklist: Updating an Assembly](../technical-guides/checklist-updating-an-assembly.md).  
  
-   If you upgrade a BizTalk Server assembly using side-by-side versioning, you will have to perform manual steps before and after using the .msi file. For more information about the manual steps that are required, see [Checklist: Updating an Application Using Side-by-Side Versioning](../technical-guides/checklist-updating-an-application-using-side-by-side-versioning.md).  
  
## Updating an Assembly  
 **Increment the version of an assembly in a production environment**  
  
- If you are updating an assembly that is running in a production environment, you should always increment the assembly version number.  
  
  **Update the GAC with an updated assembly**  
  
- When you update an assembly containing an orchestration, schema, or map, you must update the GAC with the assembly containing the new version. Otherwise, BizTalk Server will use the outdated version. To do this, on each computer that is running an instance of the host to which an application is bound, uninstall from the GAC the outdated version of the assembly containing the updated artifact and make sure that the new version is installed.  
  
  **Restart a host instance after updating an assembly**  
  
- If a BizTalk assembly in an existing application is updated, you may need to restart host instances for the changes to take effect. Restarting a host instance stops all other applications that are running on the host instance.  
  
## Updating an Artifact  
 **Undeploy a dependent artifact before the artifact that it depends on**  
  
- If you are undeploying an artifact on which another artifact depends, you must undeploy the dependent artifact first.  
  
  > [!NOTE]  
  >  If you do not undeploy the dependent artifact first, the BizTalk Server Administration console will display a warning and prevent you from undeploying artifacts in the incorrect order.  
  
  **Do not stop an artifact that another application depends on**  
  
- If you stop an artifact in one application (which may result from stopping the entire application) that another application depends on, the dependent application will not function correctly. For more information about stopping an application, see [How to Start and Stop a BizTalk Application](http://go.microsoft.com/fwlink/?LinkID=154729) (http://go.microsoft.com/fwlink/?LinkID=154729).  
  
  **Add a reference to an assembly before moving an artifact**  
  
- When you move an artifact to a new application, any other artifacts on which it has dependencies are also moved unless the new application has a reference to the application(s) containing the artifacts on which the moved artifact depends. Also, any artifacts that have dependencies on the moved artifact are moved unless the application(s) containing them have a reference to the new application. When moving an artifact, you are shown the list of other artifacts that will also be moved.  
  
## Updating Bindings  
 **Automate the reconfiguration of bindings**  
  
-   When you update an assembly in an application, its bindings are often overwritten or else the assembly may not be bound at all, forcing you to manually reconfigure bindings. You can automate this process by using a binding file. If you are updating the same version of an assembly, you can first export a binding file for the assembly, then update the assembly, then import the assembly into the application, and then reapply the previous bindings by importing the binding file. If you are updating an assembly with a newer version, you can export a binding file, edit the file to reflect the new assembly version, import the new assembly into the application, and then apply the new bindings by importing the binding file. For more information about binding files, see [How to Export Bindings to a Binding File](../technical-guides/how-to-export-bindings-to-a-binding-file.md). For more information about editing a binding file, see [Customizing Binding Files](http://go.microsoft.com/fwlink/?LinkID=155000) (http://go.microsoft.com/fwlink/?LinkID=155000).  
  
## Starting or Stopping an Application  
 **Stop an application to update artifacts**  
  
-   If you do not stop an application to update artifacts in the application, you need to temporarily halt publication to the MessageBox database by disabling endpoints, and stop and unenlist any running instances. To stop and unenlist running instances, all dehydrated or suspended instances must be either manually resumed and completed, or terminated.  
  
-   Although it is not required to stop an application in order to update an artifact or install the application, we recommend that you always stop an application when you update an artifact.  
  
## See Also  
 [How to Export Bindings to a Binding File](../technical-guides/how-to-export-bindings-to-a-binding-file.md)