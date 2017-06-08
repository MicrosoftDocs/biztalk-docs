---
title: "Managing Pre- and Post-processing Scripts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [scripts], about managing scripts"
  - "managing [scripts]"
  - "managing [resources], scripts"
  - "scripts, managing"
ms.assetid: 107ada12-fef2-4b56-8ff8-228c13761104
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Managing Pre- and Post-processing Scripts
This section provides instructions on using the BizTalk Server Administration console or the BTSTask command-line tool to manage pre- and post-processing scripts. You can create a script that you want to have run when a BizTalk application is imported, installed, or uninstalled (removed), and then add the script to the application. When you add a script, you specify whether it is a pre-preprocessing script, which runs before import, installation and after uninstallation, or a post-processing script, which runs after import or installation, and before uninstallation.  
  
 If you select the script when exporting the application, the script is included in the .msi file for the application. When you install, uninstall, or import the application, the script automatically runs, depending on how you have written the script. For more information about creating and using scripts, see [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).  
  
> [!NOTE]
>  You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks. For information about using WMI, see [WMI Class Reference](../core/wmi-class-reference.md).  
  
## In This Section  
  
-   [How to Add a Pre- or Post-processing Script to an Application](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md)  
  
-   [How to Change the Destination Location of a Pre- or Post-processing Script](../core/how-to-change-the-destination-location-of-a-pre-or-post-processing-script.md)  
  
-   [How to Remove a Pre- or Post-processing Script from an Application](../core/how-to-remove-a-pre-or-post-processing-script-from-an-application.md)