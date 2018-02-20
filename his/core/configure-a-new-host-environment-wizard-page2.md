---
title: "Configure a New Host Environment Wizard Page2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15303"
ms.assetid: 6484429e-e5db-4cb8-bb5b-2cdcc3b5f5b8
caps.latest.revision: 3
robots: noindex,nofollow
---
# Configure a New Host Environment Wizard Page
Use the **Configure a New Host Environment** wizard page to describe the basic host characteristics that are concerned with data formats. Type the name of the host environment, and then type or select the attributes of the host.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Host environment**|Type the name for the host environment. The name can be a maximum of 259 alpha-numeric characters. The name cannot be the same as that of an existing host environment. **Caution:**  If the host environment is located on the same computer as the HIP application, and the client program uses either host name **localhost** or IP address **127.0.0.1** to connect to the HIP application, the host environment should also use **localhost** or **127.0.0.1** instead of the real computer name or IP address. Failure to set the names or IP addresses identical for the host and client prevents the HIP runtime from delivering calls between the two, and causes the application to fail.|  
|**Data conversion**|Select the data conversion routine used.|  
|**Host code page**|Select the code page used by the host. Each available code page is listed by its symbolic value.|  
|**Network type**|Select the type of network used to communicate with the host. The choices are:<br /><br /> -   TCP/IP (default)<br />-   SNA|  
|**Remote endpoint manager**|The IP address of the host or the host name registered in the DNS (for a TCP/IP network); the LU name associated with the host system (for an SNA network). In either case, the name can be a maximum of 259 alpha-numeric characters.|  
  
## See Also  
 [Configure Host Environment Default Method Resolution Wizard Page](../core/configure-host-environment-default-method-resolution-wizard-page2.md)   
 [New Application Deployment Wizard](../core/new-application-deployment-wizard1.md)