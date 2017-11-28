---
title: "What Happens When Artifacts Are Imported | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "importing, artifacts"
  - "artifacts, importing"
ms.assetid: a83957df-6e16-419a-b693-87985b498cc4
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Happens When Artifacts Are Imported
This topic describes what happens to artifacts when they are imported. There are three ways to import artifacts, which are covered in this topic:  
  
-   Importing artifacts in a BizTalk .msi file into a BizTalk group or application  
  
-   Importing an .xml policy file into a BizTalk group  
  
-   Importing a binding file into a BizTalk group or application  
  
## Importing a BizTalk .msi file  
 When you import a BizTalk .msi file into a BizTalk group or application, BizTalk Server handles the artifacts that it contains as follows:  
  
-   If during import you added any references from this application to other applications in the group, the reference is added to the BizTalk Management database.  
  
-   If you specified this option, existing artifacts in the application are overwritten by artifacts in the .msi file that have the same full name and version number (if applicable).  
  
-   If binding files have been added to the application, and you select their target environment during import, the bindings are applied.  
  
-   Pre- or post-processing scripts that are configured to run on import will run.  
  
-   File-based artifact data is serialized and stored in the BizTalk Management database. This includes data for assemblies, virtual directories, files, scripts, certificates, and BAM artifacts.  
  
    > [!IMPORTANT]
    >  For security reasons, the private key is removed from each certificate when it is exported. Therefore, no private keys are stored in the BizTalk Management database.  
  
-   Policy data is stored in the Rule Engine database.  
  
-   BAM artifacts are stored in the BAM Primary Import database. BAM definitions are deployed.  
  
-   BizTalk assemblies and .NET assemblies that have the "Add to GAC on import" deployment option configured are added to the global assembly cache (GAC).  
  
> [!NOTE]
>  Because the artifact data is stored in the BizTalk Server databases, when you later export the application into an .msi file, BizTalk Server can retrieve from the databases all of the configuration information and data associated with the application and its artifacts and include it in the .msi file. When you import the .msi file into another BizTalk group, all of the artifact configuration information and data is recreated in the new group.  
  
 After you import an application, you can view, manage, and deploy the artifacts in the application either together as a single entity or individually by using the Administration console or BTSTask. For more information, see [Application Deployment and Management Tools](../core/application-deployment-and-management-tools.md).  
  
## Importing a policy  
 When you import a policy from an .xml file, the policy is added to the Rule Engine database. Unlike when you import a policy within a BizTalk .msi file, the policy is not associated with any application in the BizTalk Management database. The policy displays in the Policies node of the \<All Artifacts\> folder in the BizTalk Server Administration console. After importing the policy you can publish it to make it available for applications in the group to use. For more information, see [Managing Policies](../core/managing-policies.md).  
  
## Importing a binding file  
 When you import a binding file into a BizTalk group, any bindings that currently exist in the group having the same name as bindings in the imported file are overwritten by the bindings in the imported file, and the configuration is applied.  
  
 When you import a binding file into a BizTalk application either individually or as part of an application, any bindings that currently exist in the application having the same name as bindings in the file are overwritten by the imported bindings, and the configuration is applied.  
  
> [!IMPORTANT]
>  For security reasons, when you export a binding file, BizTalk Server removes the passwords for the bindings from the file. After importing the bindings, you must reconfigure passwords for send ports and receive locations before they will function. You configure passwords in the Transport Properties dialog box of the BizTalk Server Administration console for the send port or receive location. For instructions, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md). See also [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).  
  
## See Also  
 [What Happens to Artifacts During Application Deployment](../core/what-happens-to-artifacts-during-application-deployment.md)   
 [Importing BizTalk Applications, Bindings, and Policies](../core/importing-biztalk-applications-bindings-and-policies.md)   
 [Dependencies and Application Deployment](../core/dependencies-and-application-deployment.md)