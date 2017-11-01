---
title: "Configure a New Local Environment Wizard Page(TI)1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15312"
ms.assetid: fba1c4fd-943f-4a5a-9c02-3ce9e8a7df1c
caps.latest.revision: 3
robots: noindex,nofollow
---
# Configure a New Local Environment Wizard Page(TI)
Use the **Configure a New Local Environment** wizard page to define the basic characteristics of the new local environment. Type the name of the new local environment. To define its characteristics, select a specific network type and transport class.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Local environment**|Type the name for the local environment. The name can be a maximum of 259 Unicode characters (alphabetic, numeric, space, and special). The name cannot be the same as that of an existing local environment. The name for the new local environment is a required field, and you will receive an error message if you click **Next** without providing a name.|  
|**Network type**|Select the type of network used to communicate with the host. The choices are:<br /><br /> -   TCP/IP (default)<br />-   SNA|  
|**Transport class**|Select the class of the transport object. The list of choices changes according to the selected **Network type**. The default transport class is TCPTransport Class.|  
|**Endpoint manager**|Select or type the local LU alias to manage the endpoint. **Note:**  The Endpoint manager edit box is set to localhost and disabled if the Network type is set to TCP/IP.|  
  
## See Also  
 [Configure Local Environment Endpoints (TCP/IP) Wizard Page (TI)](../core/configure-local-environment-endpoints-tcp-ip-wizard-page-ti.md)   
 [Configure Local Environment Endpoints (SNA) Wizard Page(TI)](../core/configure-local-environment-endpoints-sna-wizard-page-ti.md)   
 [New Local Environment Wizard (TI)](../core/new-local-environment-wizard-ti.md)