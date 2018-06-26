---
title: "Manage BizTalk Assemblies | Microsoft Docs"
description: Links to work with assemblies in BizTalk Server, including adding, updating, viewing the dependencies, and removing assemblies
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62cc92f5-a1ea-46e4-88e6-b8a71a0c40a2
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Manage BizTalk Assemblies

## Overview
This section provides instructions on using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console or the BTSTask command-line tool to manage BizTalk assemblies after they have been deployed into a BizTalk group. A BizTalk assembly is a Microsoft Windows DLL file that contains resource information, such as orchestrations, pipelines, schemas, and maps to be used in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] business solution. For background information on BizTalk assemblies, see [BizTalk Assemblies](../core/biztalk-assemblies.md).  
  
> [!IMPORTANT]
>  Deploying or undeploying a property schema may expose sensitive data, and subsequently expose sensitive information during tracking. Whenever an assembly containing a property schema is deployed or undeployed, the event viewer logs an event in the Windows Application Event Log. You should check the event log for these messages to ensure that all assembly deployment activities are in line with your policies for any sensitive data. (The message generated to the Event Log for deployment is: "The user "{1}" deployed the assembly "{0}" containing property schemas." The message generated to the Event Log for undeployment is: "The user "{1}" undeployed the assembly "{0}" containing property schemas.")  
> 
> [!NOTE]
>  You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks. For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
 The developer uses [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to develop BizTalk assemblies, as described in [Developing BizTalk Server Applications](../core/developing-biztalk-server-applications.md), and can deploy them from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] as described in [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md). The developer can also manage BizTalk assemblies during the development process by using either the administration console, as described in this section.  
  
## Next steps 
  
-   [Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md)  
  
-   [Modify the Deployment Options of a BizTalk Assembly](../core/how-to-modify-the-deployment-options-of-a-biztalk-assembly.md)  
  
-   [View the Dependencies for a BizTalk Assembly](../core/how-to-view-the-dependencies-for-a-biztalk-assembly.md)  
  
-   [Remove a BizTalk Assembly from an Application](../core/how-to-remove-a-biztalk-assembly-from-an-application.md)