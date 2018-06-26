---
title: "Using Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio"
ms.assetid: 1ef68df2-5205-4d96-9e0f-0ae78800a121
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Visual Studio
Within the BizTalk project system, you can use many of the tools available in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], as well as tools designed specifically for creating applications that run on Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. This topic describes some of the common procedures that you can use to create an application that runs on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  

 When you use the BizTalk project system, you use many of the same user interface (UI) components, such as Solution Explorer and the Properties window, to create your application. Additionally, there are components, such as BizTalk Editor, that are available only after you install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. While you can use these specific [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] UI components with any project system, they specifically enable you to build applications that run on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  

 While the BizTalk project system uses many of the same menus and menu commands as other [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project systems, some commands are new, unavailable, expanded, or restricted when you use the BizTalk project system. This topic describes the various menus available in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and how they interact with the BizTalk project system.  

> [!NOTE]
>  The following topics are focused on showing the menus and menu items that behave differently from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  

## File Menu  
 Most of the **File** menu commands work the same way for BizTalk projects as for other [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects. Certain commands are unsupported or unavailable when working with the BizTalk projects. For example, the **Print** command is not supported when you are working with pipelines.  

## View Menu  
 The following table lists BizTalk project system windows, toolbars, and toolboxes available from the **View** menu.  


|   Submenu name    |  Submenu name (if applicable)   |                                                                                                                                                                               Description                                                                                                                                                                               |
|-------------------|---------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                   |                                 |                                                                                                                                                                                                                                                                                                                                                                         |
| **Other Windows** |     **Orchestration View**      | Orchestration View is an available window that enables you to add, delete, and examine orchestration parameters, ports, and port types, messages and multipart message types, correlation sets and correlation types, role links and role link types, scopes, and orchestration properties. **Note:**  This window is only available from within an open orchestration. |
| **Other Windows** |      **Expression Editor**      |                                                                             Expression Editor is an available window that is a standard [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] text editor with IntelliSense that enables you to enter complex expressions.                                                                             |
|    **Toolbox**    | **BizTalk Pipeline Components** |                                                                                             This is a list of the pipeline components that you can drag onto the pipeline design surface. You can only add pipeline components to your active pipeline that are available.                                                                                              |
|    **Toolbox**    |   **BizTalk Orchestrations**    |                                                                                                                                   This is a list of the orchestration shapes that you can drag onto the orchestration design surface.                                                                                                                                   |
|    **Toolbox**    |       **BizTalk Mapper**        |                                                                                                                           This is a list of the functoids that you can drag onto the map grid surface. The functoids are grouped by function.                                                                                                                           |
|   **Toolbars**    |       **BizTalk Editor**        |                                                                                                 A visual tool that simplifies the process of creating structured document schemas, specified in XML Schema definition language (XSD), for both XML and non-XML formats.                                                                                                 |
|   **Toolbars**    |       **BizTalk Mapper**        |                                                     A graphical user-interface tool that simplifies the process of specifying an XML document transformation, based on two schemas created with BizTalk Editor, producing an Extensible Stylesheets Language Transformations (XSLT) style sheet as compiled output.                                                     |

## Project Menu  
 The following table lists some of the commands on the **Project** menu.  


|           Submenu name            |                                                                                                                                                           Description                                                                                                                                                           |
|-----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         **Add Reference**         |                                                                                                                      Use this menu item to reference other projects, other .NET projects, or COM projects.                                                                                                                      |
|     **Add Service Reference**     |                                                                              Use this menu item to add WCF service references. You also use this item to add Web references by clicking **Advanced** on the **Add Service Reference** dialog box.                                                                               |
|      **Add Generated Items**      |                                                                                                                    Use this menu item to add a generated adapter or schema file or to consume a WCF service.                                                                                                                    |
| **Add Adapter Service Reference** | Use this menu item to browse (and search) metadata and generate .NET CLR proxy classes using the selected operations and/or types. **Note:**  This item appears in BizTalk menu only if at least one adapter (shipped with [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]) is installed on your computer. |
| **Add Consume Adapter Reference** |       Use this menu item to browse (and search) metadata from adapter and then generate XML Schemas for selected operations. **Note:**  This item appears in BizTalk menu only if at least one adapter (shipped with [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]) is installed on your computer.       |

 For information about adding Web references for BizTalk Web services, see [Adding Web References](../core/adding-web-references.md).  

## Build Menu  
 The **Build** menu contains the build commands. It also contains the command to run **Configuration Manager** to set build and deployment configuration options. To deploy a project, right click the project in Solution Explorer then click the **Deploy** command. You should use this method of deployment only when you are developing your application or if you have a simple scenario. This method of deployment does **not** keep track of versions, and you can easily overwrite previous versions of an assembly. Reusing the same version is useful in a development or testing phase, but not in the production environment. For information about deployment, see [Understanding BizTalk Application Deployment and Management](../core/understanding-biztalk-application-deployment-and-management.md).  

 To add your BizTalk artifacts to the BizTalk Management database, run the Assembly Deployment Wizard. For more information about the Assembly Deployment Wizard, see [How to Deploy a BizTalk Assembly from Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md).  

> [!NOTE]
>  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] contains a version of Dotfuscator that will take a compiled assembly and obfuscate it, renaming symbols and other identifiers in an effort to protect intellectual property. Assemblies run through this tool cannot be deployed.  

## Debug Menu  
 The BizTalk project system supports the **Debug** menu commands. For information about debugging in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Debugging Orchestrations](../core/debugging-orchestrations.md).  

## BizTalk Menu  
 When you work with a project, the **BizTalk** menu appears when you open the BizTalk Editor or the BizTalk Mapper or the BizTalk Orchestration Designer. In other words, the BizTalk menu appears when you try to edit a schema or a map or an orchestration.  

> [!NOTE]
>  You might be able to access Orchestration Designer, BizTalk Editor, and BizTalk Mapper from other project systems in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]; however, the behavior of these BizTalk tools might be unpredictable. You should use Orchestration Designer, BizTalk Editor, and BizTalk Mapper within the context of a BizTalk project.  

## Help Menu  
 The following table lists some of the commands on the **Help** menu as they pertain to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  


|            Menu command            |                                                                                                                                                                             Description                                                                                                                                                                             |
|------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          **Dynamic Help**          |                                                                                                                                This menu command opens the **Dynamic Help** tab that dynamically generates topics based on the task.                                                                                                                                |
|            **Contents**            | This menu command opens the **Contents** tab and displays all the installed Help collections. You must have the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] product documentation and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] product documentation installed to view the contents. |
| **About Microsoft BizTalk Server** |                                                                           This menu command opens the **About Microsoft BizTalk Server** dialog box. This dialog box displays the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] product information.                                                                           |
|             **Index**              |                                                                                                   The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help documentation is not accessible through the index in this release.                                                                                                    |
|             **Search**             |   There is no filter for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help documentation in this release, but if you select **(no filter)** in the **Filtered by** drop-down list, the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help documentation is available to searches.    |

## Property Pages  
 You use the property pages in the Project Designer to configure the assembly project properties and deployment properties for your BizTalk project.  

### Procedures  

##### To configure assembly project properties  

1. In Solution Explorer, select the project.  

2. On the **Project** menu, click **Properties** to activate the Project Designer.  

3. Click the **Application** tab.  

4. Click **Assembly Information** and update the desired assembly properties.  

   > [!NOTE]
   >  Use the **Signing** tab in the Project Designer to specify the key file location for the assembly if you are using certificates with your application that runs on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  

##### To configure deployment properties  

1.  Select the project for which you want to configure deployment properties.  

2.  On the **Project** menu, click **Properties** to activate the Project Designer.  

3.  Click the **Deployment** tab and update your deployment properties.  

## See Also  
 [Developer Tools](../core/developer-tools.md)