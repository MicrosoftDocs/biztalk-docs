---
title: "Manage maps | Microsoft Docs"
description: Links to work with maps in BizTalk Server, including viewing and removing maps 
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e8e3057-5a9f-4b6b-b6ee-c71b7e6a51ac
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Manage Maps

## Overview
This section provides instructions on managing maps by using the BizTalk Server Administration console. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses maps to translate the records and fields in one schema to the records and fields in another schema. Maps may be used by orchestrations, send ports, and receive ports.  

## Add maps to an application  
 Maps are built in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and compiled into BizTalk assemblies. You cannot add a map to an application individually; a map is added to an application as follows:  
  
- When you add a BizTalk assembly containing a map to the application, as described in [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).  
  
- When you import an .msi file into an application that includes a BizTalk assembly containing a map, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).  
  
- When a developer deploys into an application an assembly containing a map from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], as described in [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).  
  
  For background information about maps, see [Maps](../core/maps.md). For information about creating maps, see [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md).  
  
> [!NOTE]
>  You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks. For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## Next steps 
  
-   [View the Maps for an Application](../core/how-to-view-the-maps-for-an-application.md)  
  
-   [Remove a Map from an Application](../core/how-to-remove-a-map-from-an-application.md)