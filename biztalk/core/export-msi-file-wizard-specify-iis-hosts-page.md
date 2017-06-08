---
title: "Export MSI File Wizard, Specify IIS Hosts Page | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.appdeploy.app.export.hosts"
helpviewer_keywords: 
  - "Export MSI File Wizard, Specify IIS Hosts page"
ms.assetid: f5cdfde4-23a8-43b5-928a-df2cf433d1c9
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Export MSI File Wizard, Specify IIS Hosts Page
Use the **Specify IIS Hosts** page to specify the Web server from which to export virtual directory resources. If you selected a virtual directory to export on the previous page of the wizard, and the wizard cannot locate the virtual directory in order to include it in the .msi file, you may need to provide the host name and port number used by the Web server on this page. Otherwise, click Next to continue the wizard.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Protocol**|Indicates the protocol used for the virtual directory. You do not need to provide information in this box.|  
|**Host**|If the instructions on the page indicate that this is necessary, type the host name and port (if other than 80) used by the Web server for the virtual directory. Example: MyWebServer:81|  
|**Path**|Indicates the path of the virtual directory. You do not need to provide information in this box.|  
  
## See Also  
 [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md)   
 [What Happens When Artifacts Are Exported](../core/what-happens-when-artifacts-are-exported.md)   
 [The Application Deployment Process](../core/the-application-deployment-process.md)