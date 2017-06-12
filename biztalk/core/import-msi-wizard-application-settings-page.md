---
title: "Import MSI Wizard, Application Settings Page | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.appdeploy.app.import.settings"
helpviewer_keywords: 
  - "Import MSI File Wizard, Application Settings page"
ms.assetid: 4555894a-95d7-4d65-97a6-953c95f441dc
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Import MSI Wizard, Application Settings Page
Use the **Application Settings** page to view or select the application into which the .msi file will be imported, view the references required by the application, and select the applications, if any, to which you want to add a reference.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Application name**|If you started the Import Wizard by right-clicking an application, clicking **Import** and then clicking **MSI file**, this box displays the name of the application into which this .msi file will be imported. You cannot select a different application.<br /><br /> If you started the Import Wizard by right-clicking **Applications**, clicking **Import**, and then clicking **MSI file**, you can select the application into which to import this .msi file. From the drop-down list, select the application. The list includes the application that you are importing along with all of the applications that exist in the BizTalk group. If the application you are importing does not already exist in the group, and you select it, the application will be created and the artifacts in the .msi file added to it. Otherwise, the artifacts will be added to an existing application that you select.|  
|**Application References and Resources**|Lists the required references for the application being installed and the resources (artifacts) in this .msi file.|  
|**Available applications to add references to**|Select the check boxes of applications that are referenced by the application you are importing, as listed in the **Application References and Resources** box. If the application you are importing has a dependency on an artifact in another application, you must add a reference, or the application will not function correctly. If the application on which this application depends does not exist in the group, you must either import it into the group or add the required artifact to the application.|  
|**Overwrite resources**|Select this check box to overwrite existing resources. If you are importing bindings in this .msi file they will automatically overwrite any bindings having the same name in an existing application, even if this option is not selected.|  
  
## See Also  
 [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md)   
 [The Application Deployment Process](../core/the-application-deployment-process.md)   
 [What Happens When Artifacts Are Imported](../core/what-happens-when-artifacts-are-imported.md)