---
title: "Configure a New Local Environment Wizard Page1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15301"
ms.assetid: c998d978-3265-46f4-9042-d1e331796fed
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
robots: noindex,nofollow
---
# Configure a New Local Environment Wizard Page
Use the **Configure a New Local Environment** wizard page to identify the basic characteristics of the new local environment. Select an existing local environment from the dropdown list or type the name of the new local environment. To define its characteristics, select a specific network type and transport class.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Local environment**|Type the name for the local environment. The name can be a maximum of 259 alpha-numeric characters. The name cannot be the same as that of an existing local environment.|  
|**Network type**|Select the type of network used to communicate with the host.|  
|**Transport class**|Select the class of the transport object. The list changes according to the selected **Network type**.|  
|**Endpoint manager**|For a TCP/IP network, this is always set to the local host and disabled. For an SNA network, type the name of the LU alias. In either case, the name can be a maximum of 259 Unicode characters.|  
  
## See Also  
 [Configure Local Environment Endpoints (TCP/IP) Wizard Page](../core/configure-local-environment-endpoints-tcp-ip-wizard-page.md)   
 [Configure Local Environment Endpoints (SNA) Wizard Page](../core/configure-local-environment-endpoints-sna-wizard-page.md)   
 [New Application Deployment Wizard](../core/new-application-deployment-wizard.md)