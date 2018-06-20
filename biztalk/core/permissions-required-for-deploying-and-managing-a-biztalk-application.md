---
title: "Permissions Required for Deploying and Managing a BizTalk Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deploying [applications], security"
  - "permissions, EDI adapters"
  - "deploying, security"
  - "security, applications"
  - "security, EDI adapters"
  - "assemblies, permissions"
  - "permissions, deploying"
  - "EDI adapters, security"
  - "permissions, assemblies"
  - "security, assemblies"
  - "permissions, applications"
  - "deploying, permissions"
  - "applications, importing"
  - "applications, exporting"
  - "permissions, exporting"
  - "installing, permissions"
  - "applications, security"
  - "security, permissions"
  - "applications, installing"
  - "assemblies, security"
  - "managing, security"
ms.assetid: 4a459ff1-661d-403a-99e0-d54b82e008d0
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Permissions Required for Deploying and Managing a BizTalk Application
Application deployment includes deploying BizTalk assemblies from Visual Studio as well as importing, exporting, and installing BizTalk applications. The basic permissions you need to perform these tasks are as follows:  
  
- As a member of the BizTalk Server Administrators group, you are granted the permissions required to deploy BizTalk assemblies from Visual Studio.  
  
- As a member of the BizTalk Server Administrators group, you are granted the permissions required to import BizTalk applications into a BizTalk group. If the option to add an assembly included in the application to the global assembly cache (GAC) on import has been specified, you must also have Write permissions on the assembly folder. As a member of the local Administrators group, you have this permission.  
  
- As a member of the BizTalk Server Administrators or BizTalk Server Operators group, you are granted the permissions required to:  
  
  -   Export BizTalk applications  
  
  -   Start and stop send ports, send port groups, and orchestrations  
  
  -   Enable and disable receive locations  
  
  -   Suspend, resume, and terminate instances  
  
  -   Start and stop applications  
  
- As a member of the local Administrators group you are granted permissions to install BizTalk applications on the local computer.  
  
  You may want to provide the most restrictive permissions for users to perform these tasks. The remainder of this topic provides more details on the required permissions, as follows.  
  
- [Permissions for deploying BizTalk assemblies from Visual Studio](#BKMK_Permissions_for_deploying)  
  
- [Permissions for importing an application](#BKMK_Permissions_for_importing)  
  
- [Permissions for exporting an application](#BKMK_Permissions_for_exporting)  
  
- [Permissions for installing an application](#BKMK_Permissions_for_installing_an_application)  
  
##  <a name="BKMK_Permissions_for_deploying"></a> Permissions for deploying BizTalk assemblies from Visual Studio  
 To deploy BizTalk assemblies from within Visual Studio, you must have Write permission on the BizTalk Management database, at a minimum. You are granted this permission as a member of the BizTalk Server Administrators group.  
  
##  <a name="BKMK_Permissions_for_importing"></a> Permissions for importing an application  
 To import a BizTalk application, you must have the following permissions, at a minimum. You are granted all of the required permissions as a member of the BizTalk Server Administrators group, except that if you want to install any assemblies to the GAC, you must also have Write permissions on the assembly folder.  
  
|Item|Permissions|When Required|  
|----------|-----------------|-------------------|  
|BizTalk Management database|Read/Write|Always required.|  
|BizTalk Rule Engine database|Read/Write|Required only if the application includes rules resources.|  
|BAM database|Read/Write|Required only if the application includes BAM resources|  
|Global assembly cache (GAC)|Read/Write|Required only if the application includes assembly resources, and you specify that the assemblies are added to the GAC on import. (See Note.)|  
  
> [!NOTE]
>  When importing an assembly by using the Import Wizard, you can specify the option to add the assembly to the global assembly cache (GAC). In this case, you must have write permission on the assembly folder. For more information about the assembly folder, see [Permissions for installing an application](#BKMK_Permissions_for_installing_an_application).  
>   
>  If your application includes a script that deploys any items in addition to those listed, you must have appropriate permissions to deploy the additional items.  
  
##  <a name="BKMK_Permissions_for_exporting"></a> Permissions for exporting an application  
 To export a BizTalk application, you must have the following permissions, at a minimum. You are granted the required permissions as a member of the BizTalk Operators group.  
  
|Item|Permissions|When Required|  
|----------|-----------------|-------------------|  
|BizTalk Management database|Read|Always required.|  
|BizTalk Rule Engine database|Read|Required only if the application includes rules resources.|  
|Certificate store|Read|Required only if the application includes certificate resources.|  
|Internet Information Services|Read|Required only if the application includes virtual directory resources.|  
  
##  <a name="BKMK_Permissions_for_installing_an_application"></a> Permissions for installing an application  
 By default, members of the local Administrators group have the permissions required to install BizTalk applications on the local computer. If you want to provide more restricted permissions to users who need to install applications, the following table provides the minimum permissions that you must configure. In addition to these permissions, if your application has resources that require additional permissions to install, such as to create a new database or database table, you must also have these permissions.  
  
|Item|Permissions|When Required|  
|----------|-----------------|-------------------|  
|Certificate store|Read/Write|Required only if the application includes certificate resources.|  
|Internet Information Services|Read/Write|Required only if the application includes virtual directory resources.|  
|GAC|Read/Write|Required only if the application includes assembly resources, and you specify that the assemblies are added to the GAC on install. (See Note, below.)|  
|File system|Read/Write|Required only if a destination property has been set for a resource.|  
|Registry|Read/Write|Required if the **regsvcs** or **regasm**property is set to True for an assembly resource containing managed COM or COM+ components.|  
|Registry|Read/Write|Required if the application includes unmanaged COM resources|  
  
> [!NOTE]
>  From the BizTalk Server Administration console, you can specify that an assembly be added to the GAC on installation (right-click the assembly in the resources folder and then click Modify). If this option is specified, then installing the BizTalk application requires Write permission on the assembly folder, which contains the GAC. The path of the assembly folder is %SystemRoot%\assembly.  
  
## See Also  
 [Security Considerations for Application Deployment](../core/security-considerations-for-application-deployment.md)