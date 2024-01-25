---
description: "Learn more about: What Happens When Artifacts Are Added and Removed"
title: "What Happens When Artifacts Are Added and Removed"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# What Happens When Artifacts Are Added and Removed
This topic describes what happens when you add artifacts to an application. You can add file-based artifacts to an application by using the BizTalk Server Administration console or the BTSTask command-line tool. File-based artifacts include the following types:  
  
-   BizTalk assemblies  
  
-   .NET assemblies that are not BizTalk-specific  
  
-   Binding (.xml) files  
  
-   COM components  
  
-   Certificates  
  
-   Pre- and post-processing scripts  
  
-   Policies  
  
-   Ad hoc files, such as Readme files  
  
-   Virtual directories  
  
-   BAM artifacts  
  
> [!NOTE]
>  Send ports, send port groups, receive locations, and receive ports are not file-based artifacts and cannot be added to an application. You must create these artifacts within a given application. You can then move them to a different application, if you want. Orchestrations, schemas, maps and pipelines are all deployed and managed as part of the assemblies that contain them.  
  
 When you add an artifact to an application, the artifact is associated with the application in the BizTalk Management database, and file-based data for the artifact is added to the Management database as well. This allows you to easily transport applications and artifacts from one BizTalk group to another because you can export the application and the data for its artifacts into an .msi file from the Management database, and then import it into a Management database in a different BizTalk group.  
  
 When you add a binding file to an application, you can specify the target deployment environment in which you want the bindings to be applied. Unlike importing a binding file, when you add a binding file, its bindings are not applied.  
  
 When you add a BizTalk assembly or a .NET assembly to an application, the assembly is added to the global assembly cache if you specify this option.  
  
## See Also  
 [What Happens to Artifacts During Application Deployment](../core/what-happens-to-artifacts-during-application-deployment.md)   
 [How to Create or Add an Artifact](../core/how-to-create-or-add-an-artifact.md)   
 [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md)   
 [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md)
