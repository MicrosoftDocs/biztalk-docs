---
title: "How Environment Variables Indicate Deployment State | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "scripts, variables"
ms.assetid: 022b782b-008d-41a7-9880-d1c4e5e4015e
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How Environment Variables Indicate Deployment State
Once invoked, a pre- or post-processing script can determine in which deployment state (install, import, delete, uninstall, import rollback, or install rollback) it is running by checking the environment variables BTAD_ChangeRequestAction, BTAD_InstallMode and BTAD_HostClass.  

 The following table describes the combinations of the three variables that indicate the different deployment states.  


|       Deployment State        |     Expected Values      |
|-------------------------------|--------------------------|
|                               | BTAD_ChangeRequestAction |
| Import without overwrite flag |          Create          |
|  Import with overwrite flag   |          Update          |
|            Install            |          Update          |
|           Uninstall           |          Delete          |
|        Import rollback        |          Delete          |
|       Install rollback        |          Delete          |

## See Also  
 [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)   
 [BTAD_ChangeRequestAction](../core/btad-changerequestaction.md)   
 [BTAD_InstallMode](../core/btad-installmode.md)   
 [BTAD_HostClass](../core/btad-hostclass.md)