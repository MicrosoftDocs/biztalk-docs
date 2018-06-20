---
title: "A4SWIFT Cleanup Tool | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "A4SWIFT Cleanup tool"
ms.assetid: e694f824-6097-4d60-bc7b-b4f1a40acea0
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# A4SWIFT Cleanup Tool
The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] cleanup tool enables you to prepare a server that has the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] installed on it for a new installation of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]. The tool removes A4SWIFT artifacts such as agreements, departments, and Business Rule Engine (BRE) policies, and undeploys assemblies. Running the tool enables you to avoid manually removing many A4SWIFT artifacts, and resolves problems with undeploying assemblies that might be referenced from other assemblies.  
  
 When you run the cleanup tool, you have the choice of leaving A4SWIFT installed on the computer (the default), or uninstalling A4SWIFT after removing the artifacts. You should run the tool before uninstalling A4SWIFT.  
  
> [!CAUTION]
>  Do not use the A4SWIFT cleanup tool in a production environment. The tool is intended to be used in a single-server development environment, not in a multiserver deployment.  
  
> [!NOTE]
>  By default, the cleanup tool does not work for any other language than English. You can, however, modify the environment so that the cleanup tool works on a localized computer. Run the FormPublish tool with the t parameter and the localized string for the Templates document library, for example, **t:VorLagen** in a German environment. You can then run the cleanup tool in a localized environment.  
  
 The following must be true for the cleanup tool to run:  
  
- You must be a member the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators groups.  
  
- [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] must be installed on the server on which you run the tool.  
  
- MrsrConfiguration.dll, Shared.dll, and RuleEngineExtension.dll must be deployed on the server on which you run the tool.  
  
## What the cleanup tool does  
 The A4SWIFT cleanup tool performs the following operations:  
  
- Runs **BM Undeploy** against ForActivities.xml and MRSRBAM.xml  
  
- Removes the FrrActivities_ConnectionStrings.xml and MRSRActivities_ConnectionStrings.xml files, if they exist  
  
- Removes A4SWIFT 2.1 if it exists (if you have upgraded the server to [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)], but Setup has left A4SWIFT 2.1 installed) and deletes the A4SWIFT 2.1 folder  
  
- Undeploys all A4SWIFT assemblies  
  
- Deletes the A4SWIFT Administrator group and the A4SWIFT Users group  
  
- Deletes the A4SWIFT database  
  
- Deletes the A4SWIFT virtual directory  
  
- Runs a complete silent uninstall of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] and deletes the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] folder (if selected)  
  
  As it removes artifacts and undeploys assemblies, the cleanup tool also does the following:  
  
- Starts Internet Information Services (IIS) Admin Service in order to run  
  
- Stops and then restarts the MSSQLSERVER, SQLSERVERAGENT, BizTalk, and Enterprise Single Sign-On services  
  
#### To run the A4SWIFT cleanup tool  
  
1. Prior to running the A4SWIFT cleanup tool, undeploy any project that refers to any of the A4SWIFT default assemblies.  
  
2. Open a command prompt and move to \<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools.  
  
3. Type **A4SWIFTCleanupTool.exe** and then press **ENTER**.  
  
   > [!NOTE]
   >  When you initially run A4SWIFTCleanupTool.exe, the tool displays a help screen, and prompts you to enter a parameter. The tool will not run until you enter the parameter.  
  
4. Depending upon the actions that you want the tool to take, press one of the following keys, and then press **ENTER**:  
  
   - **0** for no actions taken (the default)  
  
   - **1** to remove all the local A4SWIFT resources on the computer, including the virtual directory and registry settings  
  
   - **2** to remove all the shared A4SWIFT resources on the BizTalk Server group, including Sharepoint Web folders, FIN message templates, BRE policies and vocabularies, BizTalk artifacts, and the A4SWIFT database  
  
   - **3** to remove all the local and shared resources  
  
   - **4** to remove all the local and shared resources and uninstall the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] product.  
  
## See Also  
 [Tools](../../adapters-and-accelerators/accelerator-swift/tools.md)