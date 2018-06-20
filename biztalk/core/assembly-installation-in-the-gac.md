---
title: "Assembly Installation in the GAC | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b12d00c-8750-4c6d-8244-e613f955a478
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Assembly Installation in the GAC
Each computer contains a global assembly cache (GAC) that contains the assemblies that are used by one or more applications on that computer. For [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to process messages during run time, the assemblies included in a BizTalk application must be present in the GACs of the computers that run the application.  
  
 If your application is isolated to one server, then assemblies need only be present in the GAC of that server. However if multiple servers host the application, then the assemblies in that application must exist in the GAC of each computer that requires access to the artifacts contained in the assembly. For example, if you deploy Assembly_A to Server_1, and then enlist Assembly_A in a host on Server_2, Assembly_A must be installed in the GAC on Server_2. If it is not, Server_2 will not be able to access Assembly_A during run time.  
  
 In particular, assemblies containing orchestrations and any assemblies that they depend on must always be installed in the GAC on servers that run instances of the host to which the orchestration is bound. In addition, assemblies containing the maps and pipelines used by a port must be installed on servers that run instances of the host serving as the adapter handler for the port.  
  
 You can specify a deployment option for each assembly to install it in the GAC when you deploy the assembly from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Alternatively, you can install an assembly in the GAC manually. In addition, you can specify deployment options to install the assembly in the GAC after it is deployed into a BizTalk application.  
  
 The following summarizes the tools and methods available to install an assembly in the GAC:  
  
- **Microsoft Visual Studio.** As previously mentioned, you can set project properties to install assemblies in the GAC automatically when you deploy them, as described in [How to Set Deployment Properties in Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md). You can also manually install assemblies in the GAC by using the Gacutil command-line tool included with [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], as described in [How to Install an Assembly in the GAC](../core/how-to-install-an-assembly-in-the-gac.md).  
  
- **BTSTask command-line tool.** When you add an assembly to a BizTalk application by using BTSTask, you can specify options to install the assembly in the GAC when the application that contains it is imported or installed. For more information, see [AddResource Command: BizTalk Assembly](../core/addresource-command-biztalk-assembly.md). Also see [AddResource Command: .NET Assembly](../core/addresource-command-net-assembly.md).  
  
- **BizTalk Server Administration console.** In the same manner as BTSTask, when you add an assembly to an application by using the Administration console, you can specify options to install an assembly in the GAC when the application that contains it is imported or installed. For more information, see [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md). Also see [How to Add a .NET Assembly to an Application](../core/how-to-add-a-net-assembly-to-an-application.md).  
  
   In addition, you can configure deployment options at any time after an assembly has been deployed into or added to an application, as described in [How to Modify the Deployment Options of a BizTalk Assembly](../core/how-to-modify-the-deployment-options-of-a-biztalk-assembly.md). When assemblies are deployed into [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] for the first time, the deployment options in the Administration console are set as follows: GAC on installation is enabled and GAC on import is disabled. If you make changes to these settings, your changes will still be in effect if the assembly is redeployed from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
- **Drag and drop.** Using Windows Explorer, you can drag and drop the assembly file into the \<*Windows folder*\>\assembly.  
  
- **Other methods.** There are other tools and methods, including using Windows installer or tools created by third-party vendors, to install an assembly in the GAC.  
  
> [!IMPORTANT]
>  So that your application functions properly, ensure that the same versions of assemblies are in the BizTalk Management database as in the GAC. If you do not always install an assembly in the GAC when you deploy it, you might have different versions in the GAC and the BizTalk Management database, which will cause processing errors during run time.  
> 
> [!IMPORTANT]
>  For information about version numbering, see "Assembly Versioning" in the .NET Framework help available from Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Note that the use of .NET policy files is not supported by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## See Also  
 [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)   
 [Understanding BizTalk Application Deployment and Management](../core/understanding-biztalk-application-deployment-and-management.md)