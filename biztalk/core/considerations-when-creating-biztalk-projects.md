---
title: "Considerations When Creating BizTalk Projects | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "projects, size"
  - "map type name"
  - "projects, naming conventions"
  - "projects, planning"
ms.assetid: f6c3dc71-105f-46af-9e6e-9a4c3b982d8c
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Considerations When Creating BizTalk Projects
This section provides information that you should take into consideration when creating BizTalk projects using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
## Avoid compilation errors caused by projects that are too large  
 The [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] compiler will not successfully compile a project if it would result in an assembly larger than 75 megabytes. When the compiler reaches a size constraint it will emit fatal error CS0013 "Unexpected error writing metadata to file \<filename>" and halt.  
  
 To avoid this problem, we recommend that projects not exceed 10 megabytes unless absolutely necessary. Why?  
  
-   Smaller projects are potentially simpler to deploy because there are fewer deployment steps. And with smaller projects the steps are more likely to be closely related -- managing trading partner discounts or handling RFPs.  
  
-   It is easier to isolate bugs, deployment issues, and other problems when using smaller projects. Finding a bug in a project with 140 schemas and many custom maps and scripts will be more difficult than finding one in a project with only 10 schemas and a few custom maps and scripts.  
  
-   Separating a large project into smaller projects can reduce complexity. The smaller projects are more manageable.  
  
-   Smaller projects compile faster.  
  
-   Splitting a large project with many unrelated schemas into smaller projects with strongly related schemas may result in better performance. This is because only some of the assemblies will be loaded at a time.  
  
## Avoid using the Project Name as the Map Type Name  
 When adding a new map to a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] do not use the project name as the type name. If you do, the compiler will generate one or more errors similar to "The type name \<name>' does not exist in the type".  
  
 To change the type name for a map from within a BizTalk project, click the map in the Solution Explorer pane, then verify the type name property in the Properties pane. If it is the same, you need to modify it making sure to change any configurations that rely on it.  
  
## Visual Studio Team System Support  
 BizTalk projects in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] do not directly support all features of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Team System. The source control features of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Team System are supported for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]. Visual SourceSafe is also fully supported for the tracking and versioning of BizTalk project artifacts.