---
description: "Learn more about: Status of File Artifacts During Deployment"
title: "Status of File Artifacts During Deployment | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "artifacts, status"
  - "deploying [artifacts], status"
ms.assetid: 6d0f7336-c2cb-4aa4-9f1d-55fb85fe78bf
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Status of File Artifacts During Deployment
You may need to know what file-based artifacts exist on the file system when a pre- or post-processing script executes. For example, you might want a post-processing script to run during uninstallation and delete a certain artifact file from the file system. File-based artifacts are artifacts that can exist as files on the local file system, in addition to their representation in the BizTalk databases. Examples of file-based artifacts are COM components, .NET assemblies, BizTalk assemblies, BAM artifacts, ad hoc files, scripts, and binding files.  
  
 The following table summarizes the status of the artifact files at each point in the deployment process.  
  
|Point in the Deployment Process|Status of Application Artifact Files|  
|-------------------------------------|------------------------------------------|  
|Pre-installation|Only files of the type System.BizTalk.File exist on the local file system.*|  
|Post-installation|All files exist on the local file system.*|  
|Pre-uninstallation|All files exist on the local file system.*|  
|Post-uninstallation|All files have been deleted from the local file system.|  
|Pre-import|No files exist on the local file system unless the application has been installed on the local computer.|  
|Post-import|No files exist on the local file system unless the application has been installed on the local computer.|  
  
 \* Files exist on the local file system only if a valid destination location was specified when the file was added to the application.  
  
## See Also  
 [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)
