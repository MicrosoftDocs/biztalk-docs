---
title: "Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: accef4b8-acdf-4043-8fd7-2db9ea752074
caps.latest.revision: 36
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application
Deploy and redeploy BizTalk assemblies from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] into a BizTalk application. You may want to do this to test the functionality of the assemblies that you have been developing and package them for handoff.  

## Overview  
 BizTalk applications provide a way to view and manage the items, called "artifacts," that comprise a BizTalk business solution. Artifacts include BizTalk assemblies (containing orchestrations, schemas, maps, and pipelines), which you can deploy into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Artifacts also include items such as .NET assemblies, certificates, scripts, Readme files, and policies, which you add to your BizTalk application by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console or the BTSTask command-line tool. The solution developer or IT administrator can then view, package, deploy, and manage the application and its artifacts as a single entity. For more information about creating, deploying, and managing BizTalk applications, see [Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md).  
  
 Before you can build and deploy a BizTalk assembly, you must create a project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and either create or add the items that you want to include in the assembly. You can create a solution in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to contain multiple projects and then build and deploy their assemblies all at once into the same application or different applications. For instructions on performing these tasks, see [How to Create BizTalk Projects](../core/how-to-create-biztalk-projects.md).  
  
 After completing these tasks, you can build, deploy, and undeploy the BizTalk assemblies by taking the following steps, as described in the topics in this section:  
  
- Configure a strong name assembly key file for each [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project.  
  
- Set deployment properties for the project, including configuring the Redeploy option to easily redeploy the assembly.  
  
- Use the Deploy command in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to build the BizTalk assemblies contained in a solution and deploy them into a BizTalk application. Alternatively, you can use the Deploy command to build and deploy an assembly in a single project, although we do not recommend doing this.  
  
- After testing the application and making necessary changes, use the Deploy command in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to rebuild and redeploy the assembly.  
  
- Install the assembly in the global assembly cache (GAC), if necessary, or remove the assembly from the GAC.  
  
- Undeploy the assembly.  
  
  After deploying one or more assemblies into a BizTalk application, you can complete the configuration of the application and deploy it into a test and then production environment. For more information, see [Development Tasks for BizTalk Application Deployment](../core/development-tasks-for-biztalk-application-deployment.md).  
  
## In This Section  
  
-   [What Happens When You Deploy an Assembly from Visual Studio](../core/what-happens-when-you-deploy-an-assembly-from-visual-studio.md)  
  
-   [Assembly Installation in the GAC](../core/assembly-installation-in-the-gac.md)  
  
-   [How to Configure a Strong Name Assembly Key File](../core/how-to-configure-a-strong-name-assembly-key-file.md)  
  
-   [How to Set Deployment Properties in Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md)  
  
-   [How to Deploy a BizTalk Assembly from Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)  
  
-   [How to Redeploy a BizTalk Assembly from Visual Studio](../core/how-to-redeploy-a-biztalk-assembly-from-visual-studio.md)  
  
-   [How to Install or uninstall an Assembly in the GAC](../core/how-to-install-an-assembly-in-the-gac.md)  