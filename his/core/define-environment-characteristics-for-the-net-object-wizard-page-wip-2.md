---
title: "Define Environment Characteristics for the .NET Object Wizard Page (WIP)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15229"
helpviewer_keywords: 
  - "15229"
ms.assetid: 7fbe9e71-7ae3-461b-9989-1a68f9b4809d
caps.latest.revision: 3
robots: noindex,nofollow
---
# Define Environment Characteristics for the .NET Object Wizard Page (WIP)
Use the **Define Environment Characteristics for the .NET Object** wizard page to define the IIS Virtual Directory in which Transaction Integrator should run.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Self-hosted**|Select this to reference the TI assembly within the application itself. No IIS security will be available, and the other options on this page will be unavailable.|  
|**ASP .NET worker process**|Select this to use IIS security.|  
|**Virtual directories**|Select an IIS virtual directory. The list is populated from enumerating the IIS Virtual Directories on the local computer.<br /><br /> Note that if you do not choose an environment, an error appears when you click **Next**. If there is no environment available, you must exit this wizard and define the appropriate environment.|  
|**Service**|Choose **Remoting only**, **Remoting and Web Service**, or **Web Service only**.|  
|**Key file for proxy**|Select the key (.snk) file that TI Manager uses to sign the proxy in the IIS virtual directory. The list is populated with files used previously.|  
  
## See Also  
 [Define Remote Environment Wizard Page (WIP)](../core/define-remote-environment-wizard-page-wip-2.md)   
 [Object Wizard (for WIP)](../core/object-wizard-for-wip-2.md)