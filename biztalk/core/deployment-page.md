---
title: "Deployment Page | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.projectsystem.deployment"
ms.assetid: cde65d26-8bff-4bf5-bcc3-3f5301be5e1b
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Deployment Page
Use the **Deployment** page to provide project deployment information.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Application Name**|Specify the BizTalk application in which to deploy the assembly.|  
|**Configuration Database**|Select a Configuration database for deployment of your project. **Note:**  The BizTalk Management database is also referred to as the BizTalk Configuration database.|  
|**Server**|Select a server from the drop-down list to select a location to deploy your BizTalk solution.|  
|**Redeploy**|Select True from the drop-down list to redeploy a configuration.<br /><br /> Default value: True<br /><br /> Type: Boolean|  
|**Install to Global Assembly Cache**|Select True from the drop-down list to register the assembly in the global assembly cache (GAC).<br /><br /> Default value: True<br /><br /> Type: Boolean|  
|**Restart Host Instances**|Specifies whether to restart all BizTalk in-process host instances on the local machine. This can be useful when debugging.|  
|**Enable Unit Testing**|Specifies whether to enable unit testing for the project. For more information see: [Unit Testing with BizTalk Server Projects](../core/unit-testing-with-biztalk-server-projects.md).|  
  
## See Also  
 [Project Designer: Deployment Tab](../core/project-designer-deployment-tab.md)