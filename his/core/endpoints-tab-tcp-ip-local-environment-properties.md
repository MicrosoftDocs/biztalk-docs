---
title: "Endpoints Tab (TCP-IP Local Environment Properties)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15330"
ms.assetid: 12d7b945-e1b2-481f-b6e7-0336f746b7bb
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
robots: noindex,nofollow
---
# Endpoints Tab (TCP/IP Local Environment Properties)
Use the **Endpoints** tab to view, add, and delete endpoints in the local environment definition.  
  
|Use this|To do this|  
|--------------|----------------|  
|**New port or service name**|Type the port number or service name for the local environment. The port number can be a maximum of 5 numeric characters and must be greater than 0 and fewer than 32768. The service name can be a maximum of 64 alpha-numeric characters. The format of the name must conform to the WinSock Service Name convention. The port number or name cannot be the same as that of an existing number or name in **Defined ports and service names**.|  
|**Add**|Click to validate the port number or service name you typed. If the number or name is valid, it then appears in **Defined ports and service names**. If the local environment is referenced by an application, the new port or service name will not be available for use until all the applications that use the local environment are restarted.|  
|**Defined ports and service names**|View the valid ports and services names for the local environment.|  
|**Remove**|Click to remove a selected port number or service name from **Defined ports or service names**.|  
  
> [!CAUTION]
>  The properties of a local environment are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the local environment to function incorrectly.  
  
## See Also  
 [Local Environments Node](../core/local-environments-node.md)   
 [Local Environment Node](../core/local-environment-node.md)   
 [TI Manager Properties](../core/ti-manager-properties.md)