---
title: "BizTalk Server Project Versioning | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dcdd5354-6335-4320-adbf-28ac934c9ce6
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Server Project Versioning
When developing with the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)], versioning is governed by a standard set of rules that work to minimize the impact of version number changes. Depending on how a [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]application or component is deployed, dependencies can be handled by an application configuration file, through XCOPY installation, or by other [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] deployment mechanisms. As the following sections will show, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adds additional complexity to versioning and dependencies.  

## Implications of Changing Version Numbers  
 In [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] development it is typical to update the assembly version number to the current build number when a build takes place. However, when developing a BizTalk solution, changing the assembly version number can break the relationship between an assembly and the dependent items that reference the DLL by its assembly version number. The following table lists items that refer to a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assembly by using its version number and the effect of changing an assembly version number.  


|                               Entity                               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               Effect of changing assembly version number                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                           Binding files                            |                                                                                                                                                                                                           Changing the assembly version number causes any existing binding files that reference the assembly to fail. This is because the binding file references the assembly by attributes including its version number.<br /><br /> You can update the version information in the binding file by using Notepad or another editor. You can also redeploy the solution and then regenerate the binding file by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. Finally, you can use scripts to automate deployment and versioning. For more information about deployment, see [Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md).                                                                                                                                                                                                            |
|            BAM tracking profile definition (.btt) files            |                                                                                                                                                                                                                                                                                                                                           Changing the assembly version number causes any existing BAM tracking profile definition files to fail. The BAM tracking files are in a binary file format so they cannot be edited and instead must be regenerated. If BAM tracking profiles are required it may be necessary to do either of the following:<br /><br /> -   Avoid frequently updating version numbers during the build process.<br />-   Delay building BAM tracking profiles until version numbers are stable.                                                                                                                                                                                                                                                                                                                                            |
| Web services published by using the Web Services Publishing Wizard | When the Web Services Publishing Wizard is used to produce an ASP.NET Web interface, the assembly version of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assembly is included in the ASP.NET source code. The assembly version number is used at run time by the ASP.NET interface as part of the **bodyTypeAssemblyQualifiedName** property of the Web service operation. If the version number of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assembly changes without updating the **bodyTypeAssemblyQualifiedName** property, then subsequent Web service operations will be rejected by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].<br /><br /> If the receive location uses the XmlDefaultPipeline, the subscription relies on the document type. It uses the embedded assembly information and will fail if the assembly does not exist. If you use the PassThruPipeline (which is the default if you expose a port and let the wizard create the receive location), the subscription ignores this embedded assembly information. |

 To find out more about [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies and deployment, see [BizTalk Assemblies](../core/biztalk-assemblies.md).  

## Approaches to Versioning  
 When planning a project, you have a choice between the following:  

- Choosing a fixed assembly version for a given deliverable and incrementing only the file version number  

- Incrementing both the assembly version and the file version during the course of development  

  These approaches are compared in the following table.  

|                                                                    Fixed assembly version, dynamic file version                                                                     |                                                            Dynamic assembly version, fixed or dynamic file version                                                            |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                Assembly version number = Fixed number<br /><br /> File version number = Build number                                                |                                             Assembly version number = Build number<br /><br /> File version number = Build number                                             |
|   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime may pick up the wrong version of the assembly if multiple assemblies are installed.    | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] always runs the latest version of the assembly, even if multiple assemblies are installed. |
|                                                            Only one version of the solution can be deployed at any time.                                                            |               Different versions of the solution can be deployed side by side (although other aspects of the solution, such as schema definitions, may clash).                |
|                                                   BizTalk Host needs to be restarted to force the loading of updated assemblies.                                                    |                               Forces [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to load new assemblies.                               |
| Requires less work to create a new deployment because files that reference the assembly version number (for example, binding files and tracking profiles) do not need to be edited. |                   Requires more work for deployment because files that reference the assembly version number need to be kept updated with the new version.                    |

 You may choose to use the fixed assembly version and dynamic file version approach if you are prototyping a system or developing any other type of non-shipping project. If you do not intend to deliver the application to an end user, you can streamline deployment tasks and reduce broken dependencies by fixing the assembly version and incrementing the file version number. For version tracking, you must remember to increment the file version number for each build.  

 If you are building a project that will be delivered to an end user, you should consider incrementing the assembly version number and, optionally, storing a meaningful file version number. While this approach incurs the added effort of modifying build numbers and associated dependencies, it ensures that the latest versions of your assemblies are used. By using automated deployment scripts, you can lessen the impact of versioning. To view deployment samples, see [Application Deployment (BizTalk Server Samples Folder)](../core/application-deployment-biztalk-server-samples-folder.md).  

> [!NOTE]
>  You should choose the versioning mechanism that ensures that the proper files are delivered and simplifies maintenance and enhancement.  

## Map Function Version Numbering  
 .NET assemblies can be invoked from within a map by using the **Scripting** functoid. This provides a great deal of flexibility and enables the developer to solve many different custom mapping problems. It also imposes a unique constraint on the map—it must internally reference not only the assembly type name but also the full assembly version number being invoked. As a consequence, if the version number of the assembly called by the map changes, all of the links that reference the assembly will break.  

 To avoid this issue we recommend that if assemblies are required to be called from a map, a specific assembly is created to hold only map functionality and the assembly version number of this assembly is fixed. In this way, other helper functions can have the assembly version updated without breaking the maps.  

 If an assembly referenced from a map is changed after map development then consider updating the map file outside of the Map Editor to reflect the updated version numbers.  

#### To use Notepad to modify the map file to reflect updated version numbers  

1.  Using the **Start** menu, launch Notepad.  

2.  In Notepad, on the **File** menu, click **Open**. In the **Open** dialog box, select the map file you want to modify, and then click **Open**.  

3.  On the **Edit** menu, click **Find**. In the **Find** dialog box, enter **Assembly=**, and then click **Find Next**.  

4.  If there is a script reference to an external assembly, Notepad should find an XML element like the following:  

    ```  
    <Script Language="ExternalAssembly" Assembly="Contoso.Scripts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c5145e4e089" Class="Contoso.Scripts" Function="CalculateValue" AssemblyPath="Contoso.Scripts.dll"/>  
    ```  

     Update the version number. If there are multiple instances, use **Replace** on the **Edit** menu.  

5.  Save the file.  

     You can now open the map using the Map Editor.  

## See Also  
 [Best Practices for Deploying a BizTalk Application](../core/best-practices-for-deploying-a-biztalk-application.md)   
 [Admin (BizTalk Server Samples Folder)](../core/admin-biztalk-server-samples-folder.md)   
 [Deploying and Starting a New Version of an Orchestration Programmatically](../core/deploying-and-starting-a-new-version-of-an-orchestration-programmatically.md)