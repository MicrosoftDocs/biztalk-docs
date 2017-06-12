---
title: "How to Update an Assembly | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4f456c8f-247a-4d5c-b5af-41e88968779c
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Update an Assembly
This topic describes how to update the version of an assembly and the application that an assembly is deployed to using Visual Studio 2010.  
  
> [!NOTE]  
>  If you are updating an assembly with a new version, you do not need to restart the application.  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.  
  
## Updating an Assembly  
  
#### To increment the version number of an assembly  
  
1.  In Solution Explorer, right-click the BizTalk project, and then click **Properties**.  
  
2.  In the **Project Designer**, click the **Application** tab.  
  
3.  In the right pane, click **Assembly Information**.  
  
4.  In the **Assembly Information** dialog box, specify values for the **Assembly Version** field to increase the assembly version number. You should increase only the major or minor version number. The major version number is the first digit in the sequence (***n***.0.0.0); the minor version number is the second digit in the sequence (0.***n***.0.0). BizTalk Server will not recognize a version number change that is later in the sequence, such as 0.0.***n***.0 or 0.0.0.***n***.  
  
5.  Click **OK** to close the **Assembly Information** dialog box.  
  
6.  Save the project.  
  
    > [!NOTE]  
    >  Use the Pipeline Designer and BizTalk Explorer Object Model to avoid schema collisions when incrementing assembly versions.  
  
#### To change the application that an assembly is deployed to  
  
1.  In Solution Explorer, right-click the BizTalk project, and then click **Properties**.  
  
2.  In the **Project Designer**, click the **Deployment** tab.  
  
3.  In the right pane, specify the application name in the **Application Name** field.  
  
4.  Ensure that the **Install to Global Assembly Cache** property is set to **True**.  
  
    > [!NOTE]  
    >  When you deploy the solution, the assemblies will be deployed into the new application and installed in the GAC.