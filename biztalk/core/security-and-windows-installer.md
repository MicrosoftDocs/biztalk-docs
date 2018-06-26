---
title: "Security and Windows Installer | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "security, Windows installer"
  - "Windows installer"
ms.assetid: efa68c3e-2006-4665-bd41-07defaf4e2e2
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Security and Windows Installer
Windows Installer is a powerful tool for installing and updating BizTalk applications. When using Windows Installer, you should be aware of the security issues that can be created by malicious Windows Installer (.msi) file creators and take steps to prevent them.  
  
 Administrators typically run .msi files, and therefore the processes that run during application installation or update have very high privileges. A malicious .msi file creator could exploit this fact in a number of ways, including the following:  
  
- Running script files that make undesirable changes to your system or files.  
  
- Overwriting the COM catalog.  
  
- Overwriting registry values. These changes cannot be rolled back.  
  
- Flooding the file system.  
  
  When dealing with .msi files, you should take the following precautions at a minimum:  
  
- Install only .msi files that you completely trust.  
  
  > [!NOTE]
  >  As a best practice, individuals who are responsible for generating .msi files should take additional steps to sign the .msi files so that users can verify that the source of the file is trusted.  
  
- Thoroughly test your .msi files before using them in a production environment.  
  
- Store the .msi files in protected folders that are secured with appropriate discretionary access control lists (DACLs).  
  
## See Also  
 [Security Considerations for Application Deployment](../core/security-considerations-for-application-deployment.md)