---
title: "Changes to BizTalk Project System in BizTalk Server 2013 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82f0dd18-073c-4cba-aa0d-48076c58f874
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Changes to BizTalk Project System in BizTalk Server 2013
This topic gives you a high-level overview of changes to the BizTalk Project System in BizTalk Server.  
  
## Project properties are displayed in project designer window  
 Properties for a BizTalk Server project are now displayed in the Project Designer of Visual Studio instead of in a Properties dialog. The Project Designer provides a centralized location for managing project properties, settings, and resources. The Project Designer appears as a single window in the Visual Studio IDE, much the same as other designers such as the Form or Class designers and contains a number of pages that are accessed through tabs on the left-hand side. For more information, see [http://go.microsoft.com/fwlink/?LinkId=190417](http://go.microsoft.com/fwlink/?LinkId=190417).  
  
## Properties for schema and map files are displayed in Properties window  
 Properties for schema and map files such as **Input Instance Filename** and **Test Map Input Instance** are displayed in the Properties window with instead of in a separate **Properties** dialog box.  
  
## Add Web Reference option on projects  
 The **Add Web Reference** option is not available when you right-click the project name or **References** in the Solution Explorer. You can add a Web reference to a Web service (.asmx) by using the following steps:  
  
1. Right-click **References** in the project, and then click **Add Service Reference**.  
  
2. In the **Add Service Reference** dialog box, click **Advanced**.  
  
3. In the **Service Reference Settings** dialog box, click **Add Web Reference**.  
  
4. Type the URL, and then click **Go**.  
  
5. Click **Add Reference** to add the Web reference.  
  
   > [!TIP]
   >  After you add a Web reference to a BizTalk project, the **Add Web Reference** menu option is available on the References, Web References and project nodes.  
  
   For more information about adding service and Web references, see [http://go.microsoft.com/fwlink/?LinkId=131577](http://go.microsoft.com/fwlink/?LinkId=131577).  
  
## MSBUILD Integration  
 Visual Studio uses the MSBUILD project file format to store build information about managed projects including BizTalk projects. For more information, see [MSBUILD Integration with Visual Studio](../core/msbuild-integration-with-visual-studio.md).  
  
## Team Foundation Server integration  
 You can use Team Foundation Server as a source control system for BizTalk projects. You can perform operations such as check-in and check-out from Solution Explorer window itself.  
  
## Support for unit testing  
 This feature allows you to unit test schemas, maps, and pipelines. For more information, see [Unit Testing with BizTalk Server Projects](../core/unit-testing-with-biztalk-server-projects.md).  
  
## Debug Map feature  
 **Debug Map feature**. You can debug a map (XSLT) by using the inline XSLT debugger with in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. For more information, see [How to Debug Maps](../core/how-to-debug-maps.md).  
  
## Migrating BizTalk Server projects  
 Visual Studio projects developed for earlier version of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can be migrated to the BizTalk Server environment by using the Visual Studio conversion wizard. For more information, see [Migrating a BizTalk Server Project](../core/migrating-a-biztalk-server-project.md).  
  
## Release and Debug build types  
 BizTalk projects now have two build types: **Release** and **Debug**, which replaces **Development** and **Deployment** of earlier versions. However, you will continue to see the **Development** and **Deployment** configurations for the projects that are migrated from [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)].  
  
## Embedding tracking and debugging information  
 The **Embed Tracking Information** and **Generate Debugging Information** output configuration properties are replaced by the **Define TRACE constant** and **Define DEBUG constant** build options on the **Build** tab of Project Designer. The **BPEL Compliance code generation** configuration property is replaced by **BPEL compliance code generation** property in the project properties window.  
  
> [!IMPORTANT]
>  The Visual Studio Conversion Wizard takes care of automatically migrates the preceding mentioned settings to new environment.  
  
## User Access Control  
 Visual Studio does not let you deploy a BizTalk project on a computer with the User Access Control (UAC) feature turned on unless you run Visual Studio with administrative privileges. To run Visual Studio with administrative privileges, click **Start**, point to **All Programs**, point to **Microsoft Visual Studio**, right-click **Microsoft Visual Studio \<version\>**, and then click **Run as administrator**.  
  
## C# files in a BizTalk project  
 BizTalk Server allows you to combine helper classes with BizTalk artifacts for flexible packaging needs only.  However, you cannot add a new C# file directly by using the **Add New Item** or **Add New Class** menu options.  
  
## GenerateCSFiles registry key is obsolete  
 The **GenerateCSFiles** registry key is obsolete now. All generated .cs files are displayed in the Solution Explorer window. You may need to click **Show All Files** toolbar item in the Solution Explorer window to see .cs files associated with some of the BizTalk items.