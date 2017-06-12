---
title: "Import MSI Wizard: Application Target Environment Settings | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.appdeploy.app.import.environment"
helpviewer_keywords: 
  - "Import MSI File Wizard, Application Target Environment Settings"
ms.assetid: b0f80f12-e530-4c53-86e6-fec8417fbdd2
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Import MSI Wizard: Application Target Environment Settings
Use the **Application Target Environment Settings** page to specify which bindings to apply to this application on import. If you added one or more binding files to the application before it was exported into the .msi file, and specified a target environment for each binding file you added, the target environments that you specified will appear in the list. Otherwise, only \<Default> will display. This option applies all of the application bindings that were exported into the .msi file and that do not have a target environment specified.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Target Staging Environment**|In the drop-down list, select the bindings to apply to this application. Select \<Default> if you want to apply all bindings in the application except for those that have a target environment specified. If the .msi file does not contain a binding file that you want to apply explicitly, you can leave \<Default> selected.|  
  
## See Also  
 [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md)   
 [How to Add a Binding File to an Application](../core/how-to-add-a-binding-file-to-an-application2.md)   
 [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md)   
 [The Application Deployment Process](../core/the-application-deployment-process.md)   
 [What Happens When Artifacts Are Imported](../core/what-happens-when-artifacts-are-imported.md)