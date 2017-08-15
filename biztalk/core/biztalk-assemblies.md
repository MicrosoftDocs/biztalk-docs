---
title: "How assemblies in BizTalk Server are deployed  | Microsoft Docs"
description: Deploy assemblies to the GAC, and enable versioning for assemblies in BizTalk Server
ms.custom: ""
ms.date: "01/21/2016"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c7f99ed5-b64a-4a38-99d7-83070fb69030
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Assemblies
The most important aspect of Microsoft BizTalk Server and the .NET Framework is that all BizTalk Server artifacts; maps, schemas, orchestrations, and pipelines, get compiled into .NET assemblies. The two most important implications of this design are that these assemblies must have strong names, and because of that, they also follow .NET versioning rules. The main implication of this is that a BizTalk project, once built against a particular version of another .NET project or assembly (including BizTalk projects), continues to use that version until it has been rebuilt against a newer version.  
  
## .NET Versioning and Assemblies  
 A common problem occurs during development related to .NET versioning when the version numbers on a BizTalk project are not changed and the assembly is redeployed without stopping and starting the BizTalk host instance that the types are loaded into.  
  
 When the process is run again, the changes do not take effect. This is due to the way in which .NET assemblies are loaded into memory. Because the host already has an in-memory copy of the assembly, it does not reload the assembly when a new copy is put into the Global Assembly Cache. For example, if version 1.0.0.0 of an assembly with an orchestration is deployed and running, and changes are made to the orchestration but the version number is not changed, then the changes do not take effect. After the host instance is stopped, the in-memory copy of the assembly is released and when the host instance starts again it reloads the new copy of the assembly and gets the changes. If a new version was deployed, say version 2.0.0.0, and it was loaded, then the changes would have taken effect.  
  
 Deploying assemblies to BizTalk Server is a two part process. The first part is traditional .NET assembly deployment in which the strong-named assembly is deployed to the Global Assembly Cache (GAC) on each server where the assembly will be used. The second step is to deploy metadata about the assemblies and their types to the BizTalk Server Management database. When BizTalk Server assemblies are loaded by BizTalk Server, they are most often loaded using their strong name, found in the Management database.  
  
## Deploying BizTalk Server Assemblies to the GAC  
 The BizTalk Server artifacts that a developer creates get compiled into classes which derive from built in BizTalk Server types. For example, an orchestration becomes a class which derives from the Microsoft.BizTalkXLANGs.BTXEngine.BTXService class. It is because these base classes are deployed in assemblies to the Global Assembly Cache, and these assemblies have dependencies on other assemblies in the GAC, that a developer's assemblies must also get deployed to the GAC.  
  
 Another important implication of BizTalk Server artifacts being deployed to the Global Assembly Cache and therefore being strong named, is that strong named assemblies cannot call other assemblies that are not also strong named. This means that any assemblies a developer creates that are used by these BizTalk Server assemblies must also be strong named. Likewise, assemblies deployed to the GAC that load other assemblies without using a specific path, must load those assemblies from the GAC.  
  
 Pipeline components are added to a developer's toolbox in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to make them available to be dragged onto the pipeline designer. When a BizTalk Server pipeline is compiled into a .NET assembly, the information about all of the components in the various stages of the pipeline get compiled into the assembly. When this pipeline is deployed to BizTalk Server, the information about the components, including their file name, is inserted into the BizTalk Management database and the pipeline assembly is deployed into the GAC. Any additional assemblies that BizTalk pipeline components depend upon must also be deployed to the GAC in order to be found at runtime. Pipeline component assemblies must also be copied to the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]\Pipeline Components directory to be accessible by a BizTalk pipeline at runtime. When the pipeline is executed, these components are loaded, and the interfaces they implement called as appropriate.  
  
## See Also  
 [Runtime Architecture](../core/runtime-architecture.md)