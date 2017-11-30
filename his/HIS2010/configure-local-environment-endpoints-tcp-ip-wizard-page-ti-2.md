---
title: "Configure Local Environment Endpoints (TCP-IP) Wizard Page (TI)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15302"
ms.assetid: 2654f81e-8ee8-4dcf-a840-472e61e57588
caps.latest.revision: 4
---
# Configure Local Environment Endpoints (TCP/IP) Wizard Page (TI)
Use the **Configure Local Environment Endpoints** (TCP/IP)wizard page to define the endpoints used to communicate with the host. To define the TCP/IP ports or service names for the local environment, type a port number or name, and then click **Add**.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Local environment**|View the name of the local environment. The name was entered on a previous page of the wizard. To change the name, click **Back**.|  
|**New port or service name**|Type the port number or service name of the local environment. The port number can be a maximum of 5 numeric characters and must be greater than 0 and less than 32768. The service name can be a maximum of 259 alpha-numeric characters. The format of the name must conform to the WinSock Service Name convention. The port number or name cannot be the same as that of an existing number or name in the **Defined ports and service names**.|  
|**Add**|Click to validate the port number or service name you typed. If the number or name is valid, it appears in **Defined ports and service names**.|  
|**Defined ports and service names**|View the existing valid ports and services names for the local environment.|  
|**Remove**|Click to remove a selected port number or service name from the **Defined ports or service names** available for use in the local environment.|  
  
## See Also  
 [Completing the New Local Environment Wizard (TI)](../HIS2010/completing-the-new-local-environment-wizard-ti-2.md)   
 [New Local Environment Wizard (TI)](../HIS2010/new-local-environment-wizard-ti-1.md)