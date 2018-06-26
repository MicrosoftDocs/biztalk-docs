---
title: "About the BizTalk Project System | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "projects, about projects"
  - "applications, creating"
  - "creating, applications"
  - "creating, business solutions"
  - "business solutions, creating"
ms.assetid: 69807e57-356e-451d-b803-4253b891b617
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# About the BizTalk Project System
You use the BizTalk project system to create part or all of a Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application or business solution. The core element of any such solution is a BizTalk project—a collection of items, such as schemas, orchestrations, Web message types, classes, pipelines, maps, and references that you can build and generate into an assembly before deploying it.  
  
 A relatively simple business solution might consist of a single BizTalk project generated into a single assembly. If your business solution is more complex—for example, you have a solution that integrates many diverse systems and processes—a possible BizTalk solution might have many assemblies generated from many BizTalk projects and deployed to several [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers.  
  
> [!IMPORTANT]
>  You cannot use commas in assembly names.  
  
 When you create a BizTalk project, you generally include one or more of the file types in the following list. These file types play specific roles in creating your solution, and the BizTalk project system provides you with a corresponding graphical design tool for each of them.  
  
- **Orchestrations.** An orchestration represents the workflow of a business process. You use the Orchestration Designer for designing orchestrations. For more information about Orchestration Designer, see [Creating Orchestrations Using Orchestration Designer](../core/creating-orchestrations-using-orchestration-designer.md).  
  
- **Schemas.** A schema describes the structure of an XML document. Schemas exchange information among applications within an organization or among trading partners. BizTalk Editor simplifies the process of defining schemas. For more information about BizTalk Editor, see [Creating Schemas Using BizTalk Editor](../core/creating-schemas-using-biztalk-editor.md).  
  
- **Maps.** A map transforms data from one format to another. BizTalk Mapper presents source schemas and destination schemas side-by-side and enables you to define transformations between data elements of different messages. For more information about BizTalk Mapper, see [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md).  
  
- **Pipelines.** A pipeline performs a variety of operations to prepare incoming or outgoing messages for further processing. Pipeline Designer enables you to implement such operations as encryption and decryption, compression, reformatting, and validation. For more information about Pipeline Designer, see [Creating Pipelines Using Pipeline Designer](../core/creating-pipelines-using-pipeline-designer.md).  
  
  BizTalk projects are compatible with Team Foundation Server (TFS). For more information about designing, developing, and deploying solutions within BizTalk Server in conjunction with TFS, see [Developing Integration Solutions using BizTalk Server and Team Foundation Server](http://www.microsoft.com/downloads/details.aspx?FamilyID=ed7bd0ee-1385-4041-8f2a-354594ee88f3&DisplayLang=en).  
  
> [!IMPORTANT]
>  TFS Build exposes a property called “MSBuild Platform” that can have 3 values – “Auto”, “x86” and “x64”. To ensure successful build, the value of the above property must be set to x86.  
  
 BizTalk projects can coexist with other projects in Visual Studio. As with all project systems in Visual Studio, BizTalk projects can include other files, such as ASP.NET pages, and can refer to other projects and assemblies that you have created. For more information about the BizTalk project template, see [BizTalk Server Project Templates](../core/biztalk-server-project-templates.md). For more information about creating BizTalk projects, see [How to Create BizTalk Projects](../core/how-to-create-biztalk-projects.md).  
  
> [!WARNING]
>  You might be able to access BizTalk design tools from other project systems that you can use in Visual Studio, but their behavior is unpredictable. Use Orchestration Designer, Pipeline Designer, BizTalk Editor, and BizTalk Mapper only within the context of a BizTalk project.  
  
## See Also  
 [Creating Orchestrations Using Orchestration Designer](../core/creating-orchestrations-using-orchestration-designer.md)   
 [Creating Schemas Using BizTalk Editor](../core/creating-schemas-using-biztalk-editor.md)   
 [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md)   
 [Creating Pipelines Using Pipeline Designer](../core/creating-pipelines-using-pipeline-designer.md)   
 [Developer Tools](../core/developer-tools.md)