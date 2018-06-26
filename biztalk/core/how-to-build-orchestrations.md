---
title: "How to Build Orchestrations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "building, orchestrations"
  - "building, solutions"
  - "building, projects"
  - "solutions, building"
  - "projects, building"
  - "orchestrations, building"
ms.assetid: f12d5da0-fbae-4f0e-85bf-1ca2e9bf7d62
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Build Orchestrations
After you have completed an orchestration drawing, you build your BizTalk project into an assembly that encapsulates an executable orchestration.  
  
 During the build process, BizTalk Orchestration Designer examines each shape to determine whether it is complete and correct, and reports an error in the task list if it is not.  
  
 You have several options for building in Visual Studio:  
  
- You can build the entire solution in which your orchestration resides.  
  
- You can build a single project within the solution.  
  
- You can skip the orchestration when building the project or solution.  
  
  If you want to build other components, including other orchestrations, but do not want to build a particular orchestration, you can indicate in the file properties for the orchestration's .odx file that you do not want to build it, and it will be skipped.  
  
### To build an orchestration  
  
-   After creating your orchestration, you need to build the BizTalk project that contains it before you can test or use the orchestration. You can build the entire solution, or a single project within the solution.  
  
### To build a solution  
  
-   In Solution Explorer, right-click the solution and select **Build Solution**.  
  
### To build a project  
  
-   Right-click a project and select **Build**.  
  
### To build a project or solution without compiling a particular orchestration  
  
-   Click the .odx file corresponding to the orchestration, and in the Properties window, click the **Build Action** property and select **None**.