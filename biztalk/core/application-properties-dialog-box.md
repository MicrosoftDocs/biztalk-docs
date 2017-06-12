---
title: "Application Properties Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.application.properties"
ms.assetid: 3b6b33e4-079c-4114-a152-cde2f9ae1cbc
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Application Properties Dialog Box
Use the **Application Properties** window to set one application as the default and to reference other applications.  
  
## General Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Name**|Type the application display name. The name must be unique.|  
|**Make this the default application**|Select this check box to set the selected application as the default application. Artifacts (such as orchestrations, ports, maps, and schemas) that were deployed without an application specified are associated with the default application. If the check box is selected and unavailable, then the current application is already the default. To make another application the default, open the **Application Properties** window for that application and select the **Make this the default application** check box.|  
|**Description**|Type any text that will help you distinguish this application from others. The maximum number of characters allowed is 1024.|  
  
## References Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**This application refers to the following applications**|Displays a list of application references that have been added to this application. You add application references in the **Add Application References** dialog box.|  
|**Add**|Click to add a new application reference to the current application.|  
|**Remove**|Click to remove the selected application reference.|  
|**The following applications depend on this application**|Displays a list of applications that reference the current application.|  
  
## See Also  
 [How to Install a BizTalk Application](../core/how-to-install-a-biztalk-application.md)   
 [Understanding BizTalk Application Deployment and Management](../core/understanding-biztalk-application-deployment-and-management.md)   
 [Importing BizTalk Applications, Bindings, and Policies](../core/importing-biztalk-applications-bindings-and-policies.md)   
 [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md)   
 [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md)