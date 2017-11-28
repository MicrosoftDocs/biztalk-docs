---
title: "How to Deploy Tracking Profiles with the Tracking Profiles Management Utility | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tracking profiles, deploying"
  - "deploying, tracking profiles"
  - "bttdeploy.exe [BAM]"
  - "managing [BAM], deploying tracking profiles"
ms.assetid: b3023379-cae1-45fc-a773-2660d3e4abf1
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Deploy Tracking Profiles with the Tracking Profiles Management Utility
A business manager asks a solutions developer to create a new tracking profile or modify an existing one to better manage and monitor a specific business process for your organization.  
  
 The solutions developer uses the Tracking Profile Editor (TPE) to define the data that the business analyst requires.  
  
 After a solutions developer creates or modifies the tracking profile, an administrator uses the bttdeploy.exe command line utility to deploy it so that the changes take affect and the data is collected. The solutions developer can deploy tracking profiles with the TPE.  
  
> [!IMPORTANT]
>  You must deploy the assemblies associated with the tracking profile before you deploy the tracking profile.  
  
> [!IMPORTANT]
>  You must have BizTalk® Administrator privileges to use this tool.  
  
### To deploy the tracking profile from the command-line utility  
  
1.  From a command prompt, move to the directory \<installation path\>\Program Files\Microsoft BizTalk Server \<version\>\Tracking\\.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
2.  Type **bttdeploy.exe \<profile name\>.btt**.  
  
3.  Press ENTER.  
  
## See Also  
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM Security Recommendations](../core/bam-security-recommendations.md)   
 [Business Activity Monitoring (BAM)](../core/business-activity-monitoring-bam.md)