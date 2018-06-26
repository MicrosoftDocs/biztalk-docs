---
title: "How to Deploy a BizTalk Assembly from Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 69d70c52-3e71-4eb2-876e-b467c7ca24b7
caps.latest.revision: 39
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Deploy a BizTalk Assembly from Visual Studio
This topic provides instructions on using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer or the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt to deploy the BizTalk assemblies from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] into a BizTalk application. Although you can deploy a single assembly from the project level (such as by right-clicking the project and clicking Deploy) or deploy all of the assemblies in the solution at once from the solution level (such as by right-clicking the solution and clicking Deploy), we strongly recommend deploying all of the assemblies at once from the solution level.  
  
 With previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], if you wanted to deploy a multiple assemblies in a solution, and any of the assemblies had a dependency on any of the other assemblies, you had to individually deploy the assemblies in the reverse order of their dependencies. For example, if Assembly1 had a dependency on Assembly2, you had to deploy Assembly2 first, and then you could deploy Assembly1.  
  
 This is still the case when you deploy assemblies from the project level. With BizTalk Server, however, when you deploy assemblies from the solution level rather than the project level, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] automatically takes care of all of the deployment steps, including deploying assemblies in the correct order. Therefore, to simplify deployment, when another assembly has a dependency on the assembly that you are deploying, you should deploy your assemblies at the solution level.  
  
 When you select the option to deploy a project or solution from within [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], the assembly or assemblies are automatically built and deployed into the specified BizTalk application in the local BizTalk group. If the application does not already exist in the group, deployment also creates the application. The assemblies and the artifacts they contain are registered and their data stored in the BizTalk Management (configuration) database for the BizTalk group. In addition, if you specify this option in deployment properties for the project, the assemblies are added to the global assembly cache (GAC).  
  
 An "artifact" is any item included in a BizTalk application, including resources you work with in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], such as assemblies and orchestrations as well as other items you create or add later after deploying the application, such as send and receive ports, certificates, and scripts. After the assembly has been deployed, you can view and manage its artifacts in the Applications node of [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] console. Each application is stored in its own folder, with subfolders displaying the artifacts in the application. For more information, see [Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md). For more information about creating and managing applications, see [Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md).  
  
 Before you deploy an assembly, you must take the following steps:  
  
-   Create a strong name assembly key file and assigned it to each project, as described in [How to Configure a Strong Name Assembly Key File](../core/how-to-configure-a-strong-name-assembly-key-file.md).  
  
-   Set deployment properties for the project, as described in [How to Set Deployment Properties in Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md).  
  
-   If you have previously deployed the assembly, enable the redeployment option for the project. For instructions and other important information about redeployment, see [How to Redeploy a BizTalk Assembly from Visual Studio](../core/how-to-redeploy-a-biztalk-assembly-from-visual-studio.md).  
  
> [!IMPORTANT]
>  You should never perform the tasks described in this topic on a production computer. During the development process, the developer often must redeploy assemblies from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. To enable the redeployment, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] may undeploy, unbind, stop, and unenlist artifacts that exist in the same or different applications. Although this is necessary and appropriate in the development environment, it can cause unexpected and undesired consequences in a production environment. In addition, to avoid the possibility of anyone's attempting to deploy an assembly from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] on a production computer, we recommend that you not install [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] on a production computer.  
> 
> [!NOTE]
>  .NET Framework runtime security policy prevents deploying assemblies from a network share by default. If you attempt to deploy an assembly from a network share and experience difficulty, see your .NET Framework security administrator, or consult "Security Policy Management" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Combined Collection.  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group. If, in **Deployment** properties, you have enabled the option to install an assembly to the global assembly cache (GAC), then you also need Read/Write permissions on the GAC. The Administrators account on the local computer has this permission. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## To deploy a BizTalk assembly or assemblies  
  
#### Using Visual Studio Solution Explorer  
  
- In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, right-click a BizTalk project or solution, and then click **Deploy**.  
  
   The assembly in the project or assemblies in the solution are deployed into the specified BizTalk application. The status of the build and deployment process displays in the lower left corner of the page.  
  
#### Using the Visual Studio command prompt  
  
1.  Start **Visual Studio Command Prompt**.  
  
2.  Type the following command, substituting the appropriate values, as described in the following table:  
  
     **devenv /deploy**  *SolnConfigName* *SolutionName* [**/project** *ProjName*] [**/projectconfig** *ProjConfigName*]  
  
     Example:  
  
     **devenv /deploy Release "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /project "MyBizTalkApp\MyBizTalkApp.csproj" projectconfig Release**  
  
    |Parameter|Value|  
    |---------------|-----------|  
    |**/deploy**|Deploys a solution after a build or rebuild.|  
    |*SolnConfigName*|Name of the solution configuration that will be used to build the solution named in SolutionName.|  
    |*SolutionName*|Full path and name of the solution file.|  
    |**/project**  *ProjName*|Path and name of the project file within the solution. You can enter a relative path from the SolutionName folder to the project file, or the project's display name, or the full path and name of the project file.|  
    |**/projectconfig**  *ProjConfigName*|Name of a project build configuration to be used when building the project.|  
  
     The first time you deploy an assembly containing an orchestration, you may receive a warning message that the orchestration is not contained in the binding file. This is because orchestrations are not automatically bound to the host upon deployment. You must perform this step manually.  
  
## See Also  
 [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)