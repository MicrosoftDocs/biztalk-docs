---
title: "Configure a New Local Environment Wizard Page(TI)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15301"
ms.assetid: fa3fe98e-700f-4ed9-bcde-e03efa8948ae
caps.latest.revision: 4
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
 [Configure Local Environment Endpoints (TCP/IP) Wizard Page (TI)](../HIS2010/configure-local-environment-endpoints-tcp-ip-wizard-page-ti-2.md)   
 [Configure Local Environment Endpoints (SNA) Wizard Page(TI)](../HIS2010/configure-local-environment-endpoints-sna-wizard-page-ti-2.md)   
 [New Local Environment Wizard (TI)](../HIS2010/new-local-environment-wizard-ti-1.md)