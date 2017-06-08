---
title: "Using Pre- and Post-processing Scripts to Customize Application Deployment | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "customizing, applications"
  - "applications, customizing"
  - "scripts, applications"
  - "scripts, customizing"
ms.assetid: 47627394-d594-491b-9098-38c5d028a378
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Pre- and Post-processing Scripts to Customize Application Deployment
The topics in this section describe how to create pre- or post-processing scripts to perform actions when an application is imported, installed, or uninstalled. Pre-processing scripts perform an action or set of actions before application import or installation starts, and after uninstallation completes. Post-processing scripts perform an action or set of actions after application import or installation completes, or before uninstallation starts.  
  
 You might, for example, want to include a pre-processing script that will run before installation to back up resource files before they are overwritten during installation. Or you might want to run a post-processing script to add a certificate to the certificate store after an application is installed.  
  
> [!NOTE]
>  BizTalk Server includes sample pre- and post-processing scripts. For information about using the sample scripts, see [Template (Application Deployment Sample)](../core/template-application-deployment-sample.md).  
  
## In This Section  
  
-   [Creating a Pre- or Post-processing Script](../core/creating-a-pre-or-post-processing-script.md)  
  
-   [How Environment Variables Indicate Deployment State](../core/how-environment-variables-indicate-deployment-state.md)  
  
-   [Status of File Artifacts During Deployment](../core/status-of-file-artifacts-during-deployment.md)  
  
-   [Pre- and Post-processing Script Environment Variables](../core/pre-and-post-processing-script-environment-variables.md)