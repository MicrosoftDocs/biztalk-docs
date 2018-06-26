---
title: "Development Tasks for BizTalk Application Deployment | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "developing, deploying"
  - "deploying [applications], developing"
  - "applications, tasks"
  - "deploying [applications], warnings"
  - "applications, developing"
  - "developing, tasks"
ms.assetid: b441d4f4-122e-4caf-8381-723c6142b0b6
caps.latest.revision: 28
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Development Tasks for BizTalk Application Deployment
The following are the steps involved in deploying BizTalk assemblies from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] into a BizTalk application, completing the application, and preparing it for deployment to the test environment. This deployment scenario is common in a development environment, where a programmer is developing and debugging a particular BizTalk business solution.  
  
> [!IMPORTANT]
>  You should never perform the tasks described in this topic on a production computer. During the development process, the developer often must redeploy assemblies from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. To enable the redeployment, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] may undeploy, unbind, stop, and unenlist assemblies that exist in the same or different applications. Although this is necessary and appropriate in the development environment, it can cause unexpected and undesired consequences in a production environment. In addition, to avoid the possibility of anyone's attempting to deploy an assembly from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] on a production computer, we recommend that you not install [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] on a production computer.  
  
1. **Develop and build the BizTalk assemblies.** You begin by creating your BizTalk business solution in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], using orchestrations, schemas, maps, and pipelines. In working on the solution, you build it into one or more BizTalk assemblies. For more information, see [Developing BizTalk Server Applications](../core/developing-biztalk-server-applications.md). You also develop and build any non-BizTalk .NET assemblies that are required for your solution to function.  
  
2. **Set deployment properties.** When you are ready to deploy your BizTalk assemblies, you set deployment properties on each [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project in the solution. In addition to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] properties (Server, Configuration, Database, Redeploy, Restart Host Instances, and Install to Global Assembly Cache), you can also set the Application Name property. This property specifies to which BizTalk application you are deploying each assembly. If Application Name is blank, the assembly is deployed into the default application. For more information, see [How to Set Deployment Properties in Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md). You must deploy your non-BizTalk .NET assemblies by adding them to the BizTalk application. This is a separate step, described later, in step 4.  
  
3. **Deploy the BizTalk assemblies to BizTalk Server running on the local computer.** You can deploy the BizTalk assemblies from a menu option, by right-clicking a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] solution and selecting the Deploy command. This builds the BizTalk assemblies in the projects contained in the solution and adds them to the BizTalk application defined in deployment properties for each project. If the application does not already exist, it is created. The assemblies and their resources, which are called "artifacts," are also deployed into the BizTalk Management database for the group, and you can view and manage them by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console or other tools. For more information about this step, see [How to Deploy a BizTalk Assembly from Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md).  
  
4. **Add artifacts that are required for the application to function correctly.** From within the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, you can easily modify an application to complete it, for example by adding and removing artifacts such as send and receive ports, scripts, policies, non-BizTalk .NET assemblies, and so forth. For more information, see [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md).  
  
5. **Factor the artifacts into multiple applications.** During the development process, you may have deployed your assemblies into a single application for convenience. For various reasons, you may want to factor the artifacts into multiple applications before they are deployed into production. For more information about best practices for factoring applications, see [Best Practices for Deploying a BizTalk Application](../core/best-practices-for-deploying-a-biztalk-application.md).  
  
6. **Create .msi files for all applications in the solution and install them locally.** You can either use the Export Wizard, available from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console or the BTSTask command-line tool to create an .msi file that contains each application's artifacts. For more information, see [Exporting BizTalk Applications, Bindings, and Policies](../core/exporting-biztalk-applications-bindings-and-policies.md). You can take the additional step of installing the artifacts from the .msi files if you want to run the solution on the local computer and verify that it is functioning as expected. For more information, see [How to Install a BizTalk Application](../core/how-to-install-a-biztalk-application.md). Verify that the solution functions as expected.  
  
7. **Redeploy the BizTalk assemblies as needed.** In the process of developing and debugging your BizTalk assemblies, you may need to redeploy them multiple times. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides a simple mechanism for redeployment. For more information, see [How to Redeploy a BizTalk Assembly from Visual Studio](../core/how-to-redeploy-a-biztalk-assembly-from-visual-studio.md).  
  
8. **Export binding files and add them back into the applications (optional).** To make it easier to import the applications back into your development environment at a later time to make changes or additions, you may want to export the bindings for each application and then add them back into the applications, specifying a Development target environment for the bindings. When you later import the application .msi files back into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on your development computer, you can specify that these bindings be applied. For more information, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).  
  
9. **Generate an .msi file for each application to hand off to your test team**. Once you have finished developing and debugging your BizTalk solution, you can use the Export Wizard or BTSTask to generate the application .msi files, as described earlier in step 6. You should import these files into a different BizTalk group in your development environment, install them, and then verify that the solution is functioning as expected. You can then hand off to your test team the .msi files, which they can use to import the applications into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] running on test computers, as well as to install them, as described in [Testing Tasks for BizTalk Application Deployment](../core/testing-tasks-for-biztalk-application-deployment.md).  
  
## See Also  
 [Application Deployment Tasks](../core/application-deployment-tasks.md)