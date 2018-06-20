---
title: "Migrating a BizTalk Server Project | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a4dde72-6555-4bf6-b90e-676aa65312ff
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Migrating a BizTalk Server Project
[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects developed for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can be migrated to the newer environments by using  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] conversion. For a list of the supported migration versions, see [Supported Upgrade Paths and Installation Guides](http://social.technet.microsoft.com/wiki/contents/articles/28554.biztalk-server-supported-upgrade-paths-and-installation-guides.aspx).  

## BizTalk Project Changes After Running the Conversion Wizard  
 The following table shows how [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] project configuration names change, and where some specific configuration properties relocate after the project is converted to a newer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project. Most of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-related project settings are located on the **Deployment** tab of Project Designer.  


| [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] project | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project |
|--------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
|             **Embed Tracking Information** output configuration property             |      **Define TRACE constant** build option on the **Build** tab of Project Designer       |
|           **Generate Debugging Information** output configuration property           |      **Define DEBUG constant** build option on the **Build** tab of Project Designer       |
|              **BPEL Compliance** code generation configuration property              |       **BPEL Compliance** code generation property in the project properties window        |

> [!NOTE]
>  BizTalk projects now have two build types: **Release** and **Debug**, which replaces **Development** and **Deployment** of earlier versions. However, you will continue to see the **Development** and **Deployment** configurations for the projects that are migrated from [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)].  
> 
> [!CAUTION]
>  Only the *.btproj and \*.btproj.user project files are backed up as a result of choosing the back up option during the conversion. Other files must be manually backed up.  
> 
> [!CAUTION]
>  Any customizations to auto-generated items such XSD and ODX files will be lost during conversion. This applies to XSD files generated when a web reference is added to a BizTalk project as well.  

## Project Migration and Delay Signing  
 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] projects that use [Delay Signing](http://go.microsoft.com/fwlink/p/?LinkId=140992) may fail during the build process after being converted for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. This can happen if **Generate serialization assembly** build setting for the migrated project configuration is not set to **Off**.  

## Project Migration and MSMQT  
 MSMQT is no longer part of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. For more information on how this can affect project migration, see the topic [MSMQT Deprecation](../core/msmqt-deprecation.md).  

## Project Conversion requires the project and solution file  
 If you attempt to convert a [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] project and do not have the solution file you will receive the following error:  

 **Error converting project file. Child element \<BIZTALK\> of element \<VisualStudioProject\> is not valid.**  

 Project conversion requires the solution file (.sln) from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project. If the solution file is not available, you must create one with [!INCLUDE[btsVStudioNet2005](../includes/btsvstudionet2005-md.md)] and add the [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] project to the solution. Then run the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] conversion wizard.  

> [!NOTE]
>  You may be able to convert the project using only the project file (.btproj) with Visual Studio.