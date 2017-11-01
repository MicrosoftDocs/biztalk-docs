---
title: "Configure Local Environment Endpoints (TCP-IP) Wizard Page (TI)1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cb10a2f6-aa96-4d58-a0c2-7c2ea5aa1dee
caps.latest.revision: 3
robots: noindex,nofollow
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
 [Completing the New Local Environment Wizard (TI)](../core/completing-the-new-local-environment-wizard-ti.md)   
 [New Local Environment Wizard (TI)](../core/new-local-environment-wizard-ti.md)