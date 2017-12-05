---
title: "General Tab (Application Properties)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15324"
ms.assetid: 9a389a1a-b58b-416e-8db8-cb5b2f0ae2cf
caps.latest.revision: 4
---
# General Tab (Application Properties)
The **General** tab allows you to set the general properties of the application.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Application**|View the name of the application.|  
|**Computer**|View the name of the computer running the application.|  
|**Process ID**|View the process ID of the HIPService. **0** indicates that HIPService is not running.|  
|**Worker threads**|Type the number of processing threads to be used in the work of the application. The number of threads must be greater than 0 and fewer than 257.|  
|**Queued requests**|Type themaximum number of requests that can be stored in the queue before new requests are rejected. The number of queued requests must be equal to or greater than the number of worker threads, and must be less than 2049.|  
|**Comment**|Type additional information about the use of the object view in the HIP environment. The comment can be a maximum of 259 alpha-numeric characters.|  
|**Service starts automatically**|Select this option to start the HIPService automatically at startup. Clear the check box to require manual start up.|  
  
> [!CAUTION]
>  The properties of an application are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the application to function incorrectly.  
  
## See Also  
 [Application](../HIS2010/application2.md)   
 [TI Manager Properties](../HIS2010/ti-manager-properties1.md)