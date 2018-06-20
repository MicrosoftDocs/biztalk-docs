---
title: "Deploying an Assembly | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 65f8ee21-0e52-4a74-b114-864a3069659c
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Deploying an Assembly
Deploying an assembly builds the assembly and imports it, along with the orchestrations, pipelines, schemas, and maps (artifacts) that it contains into the local BizTalk Management database. Initially, this is done in the development environment.  
  
 Deployment also associates the assembly with the BizTalk application that you have specified in project properties within Visual Studio. After you deploy a solution, you can view and manage the deployed assemblies and their artifacts from within the BizTalk Server Administration console or by using the BTSTask command-line tool. You can manage the artifacts either individually or grouped within the application.  
  
## Deploying an Assembly  
 You can add assemblies to applications in the following ways:  
  
- Deploy an assembly to an application from within the Visual Studio environment  
  
- Manually add BizTalk Server assemblies to the application from within the BizTalk Server Administration console  
  
- Add a BizTalk assembly to an application by using script from the command line  
  
- Move BizTalk Server assemblies from other applications from within the BizTalk Server Administration console  
  
  For more information about adding assemblies to applications, see [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](http://go.microsoft.com/fwlink/?LinkID=154719) (http://go.microsoft.com/fwlink/?LinkID=154719).  
  
## Redeploying Assemblies  
 In the process of developing and debugging your BizTalk assemblies, you may need to redeploy them multiple times. BizTalk Server provides a simple mechanism for redeployment. If you are redeploying an assembly without changing the version number, you can use the Redeploy property. BizTalk Server will automatically perform all of the steps to redeploy the assembly for you.  
  
 For more information about redeploying assemblies, see [How to Redeploy a BizTalk Assembly from Visual Studio](http://go.microsoft.com/fwlink/?LinkID=154720) (http://go.microsoft.com/fwlink/?LinkID=154720).  
  
### Best Practices for Redeploying an Assembly  
 **You must install the new assembly in the GAC**  
  
- When you redeploy an assembly, you must always install the new version of the assembly in the global assembly cache (GAC). You can do this after you redeploy it. For more information, see [How to Install an Assembly in the GAC](http://go.microsoft.com/fwlink/?LinkID=154828) (http://go.microsoft.com/fwlink/?LinkID=154828).  
  
  **You should always redeploy at the solution level when there are dependencies**  
  
- If you have multiple assemblies in a solution, and one or more assemblies in the solution has a dependency on the assembly that you want to redeploy, you should redeploy your assemblies at the solution level. This is because when you redeploy an assembly at the project level, BizTalk Server will stop, unenlist, unbind, and remove the artifacts in all assemblies that either depend on this assembly or on upon which this assembly depends. BizTalk Server will not take the additional steps to deploy, bind, enlist, and start the artifacts. When you redeploy the entire solution, however, BizTalk Server automatically takes the steps required to undeploy and redeploy all of the artifacts in the solution based on their dependencies.  
  
  **You may need to manually redeploy dependent assemblies**  
  
- BizTalk Server always undeploys dependent assemblies when it undeploys an assembly, but in the following cases, you must take the additional steps to deploy, bind, and enlist the artifacts in each dependent assembly after redeploying the assembly on which the assembly depends:  
  
   If you redeploy an assembly at the project level and another assembly in the same solution depends on it.  
  
   If you redeploy an assembly at the solution level, but a dependent assembly exists in a different solution.  
  
  **You must restart host instances**  
  
- When you redeploy an assembly that contains an orchestration without changing the assembly version number, the existing assembly is overwritten in the BizTalk Management database. Before the change will take effect, however, you must restart each host instance of the host to which the orchestration is bound. You can specify the option that all host instances on the local computer restart automatically when you redeploy an assembly.  
  
   When you redeploy an assembly that contains an orchestration without changing the assembly version number, the existing assembly is overwritten in the BizTalk Management database. Before the change will take effect, however, you must restart each host instance of the host to which the orchestration is bound. You can specify the option that all host instances on the local computer restart automatically when you redeploy an assembly. For more information about deployment properties, see [How to Set Deployment Properties in Visual Studio](http://go.microsoft.com/fwlink/?LinkID=154718) (http://go.microsoft.com/fwlink/?LinkID=154718).  
  
   You can also manually stop and start each host instance. For more information about stopping and starting a host instance, see [How to Stop a Host Instance](http://go.microsoft.com/fwlink/?LinkID=154829) (http://go.microsoft.com/fwlink/?LinkID=154829) and [How to Start a Host Instance](http://go.microsoft.com/fwlink/?LinkID=154830) (http://go.microsoft.com/fwlink/?LinkID=154830).