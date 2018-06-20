---
title: "Application Deployment and Management Features | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "what's new, Installation Wizard"
  - "what's new, BTSTask command-line tool"
  - "what's new, Import Wizard"
  - "deploying, what's new"
  - "what's new, Export Wizard"
  - "what's new, deploying"
  - "applications, what's new"
  - "what's new, applications"
ms.assetid: 2d09d6b1-1003-406f-81da-14e21a1cbc81
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Application Deployment and Management Features
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes several features to assist with the deployment of BizTalk business solutions:  
  
- **BizTalk application.** A BizTalk application provides a way to view and manage the items, called "artifacts," that make up a BizTalk business solution. Artifacts include the assemblies, orchestrations, maps, schemas, security certificates, business rules policies, BAM configuration files, bindings, scripts, and so forth that are necessary for a business solution to function. You can add artifacts to a BizTalk application and then view, package, deploy, and manage all of an application's artifacts as a single entity from within the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. You can create one, two, or more BizTalk applications to manage the artifacts in your business solution. You can use the Export Wizard to export the application and its artifacts, and then use the Import Wizard to import the .msi into another BizTalk group to recreate it there. You can then use the Installation Wizard to install the application. These wizards are described later in this topic. Each deployment procedure in this documentation includes instructions for using the Administration Console. You can also use the BTSTask command-line tool for many administrative tasks, and this documentation includes procedures for using BTSTask as well.  
  
- **Import Wizard.** You use the Import Wizard, available from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, to import artifacts from an .msi file into a BizTalk application. If the specified application does not already exist, the Import Wizard creates it. The wizard also registers and stores the artifacts in the .msi file in the BizTalk Management database. For more instructions on using the Import Wizard to import artifacts, see [Importing BizTalk Applications, Bindings, and Policies](../core/importing-biztalk-applications-bindings-and-policies.md).  
  
- **Installation Wizard.** You can start the Installation Wizard as a final step of the Import Wizard. This wizard installs the application on the local computer, so that you can run the application on the local computer. For instructions, see [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md). You can also start the Import Wizard by double-clicking an application .msi file. For more information, see [How to Install a BizTalk Application](../core/how-to-install-a-biztalk-application.md).  
  
- **Export Wizard.** You use the Export Wizard, also available from the BizTalk Server Administration console, to generate an .msi file from a BizTalk application. You can then use the Import Wizard to import the .msi file into a different BizTalk group. This makes it easy to add resources to an application, or automatically create an application on the new BizTalk group. For more information about using the Export Wizard, see [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).  
  
- **BTSTask command-line tool.** BTSTask supports the application deployment features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], allowing you to perform many operations from the command line. For more information, see [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md).  
  
  To help you become familiar with these application deployment features, we recommend that you perform the steps in [Walkthrough: Deploying a Basic BizTalk Application](../core/walkthrough-deploying-a-basic-biztalk-application.md).  
  
## See Also  
 [Understanding BizTalk Application Deployment and Management](../core/understanding-biztalk-application-deployment-and-management.md)