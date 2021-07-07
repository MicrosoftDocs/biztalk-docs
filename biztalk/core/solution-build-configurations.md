---
description: "Learn more about: Solution Build Configurations"
title: "Solution Build Configurations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords:
  - "Configuration Manager"
  - "building, solutions"
  - "building, Configuration Manager"
  - "solutions, deploying"
  - "deploying, building"
  - "solutions, developing"
  - "solutions, build configuration"
ms.assetid: 6f2cce47-388d-4c93-9146-768f53b8207e
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Solution Build Configurations
As with other projects that you build in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], you can use Configuration Manager to specify solution build configurations. Solution build configurations enable you to determine which projects to include in builds of a solution and if they will be deployed. BizTalk Server supports both **Debug** and **Release** build configurations.

 A solution build configuration with a check mark in the **Build** column enables you to build a solution and to generate an assembly when you are finished. If a check mark is also present in the **Deploy** column, then the application will be deployed based on deployment settings in the Project Designer.

 A complete reference to Configuration Manager and the configuration options provided by the dialog box can be found at the following reference link: [https://go.microsoft.com/fwlink/?LinkId=125365](/previous-versions/visualstudio/visual-studio-2010/t1hy4dhz(v=vs.100)).

### To configure build properties in Configuration Manager

1.  On the **Build** menu, click **Configuration Manager**.

2.  In the **Configuration Manager** dialog box, select one of following to configure the build properties.

    |Use this|To do this|
    |--------------|----------------|
    |**Configuration**|Choose from **Release** or **Debug** configurations for the project. Alternatively, create a new configuration or edit an existing one.|
    |**Platform**|Choose a platform for the project representing the CPU architecture of the compiled assembly. Alternatively, create a new platform or edit an existing one.|
    |**Build**|Check the box in this column for a project to have the project built or rebuilt in response to a build command for the solution.|
    |**Deploy**|Check the box in this column to have the project deployed based on deployment settings when a build command is issued for the solution or project.|

## See Also
 [How to Deploy a BizTalk Assembly from Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)
 [How to Create BizTalk Projects](../core/how-to-create-biztalk-projects.md)