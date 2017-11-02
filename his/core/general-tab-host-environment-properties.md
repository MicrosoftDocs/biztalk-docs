---
title: "General Tab (Host Environment Properties)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15331"
ms.assetid: 5bea8532-d5a2-4600-b224-dd72c93b6547
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
robots: noindex,nofollow
---
# General Tab (Host Environment Properties)
The **General** tab defines the basic characteristics of the host environment that will initiate requests to the Windows platform.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Host environment**|Type the name for your host environment. The name can be a maximum of 259 Unicode characters (alphabetic, numeric, space, and special). The name cannot be the same as that of an existing host environment.|  
|**Time-out in seconds**|The **Send** and **Receive** time-out values are used by the host-initiated processing (HIP) runtime environment when it communicates with the host environment. The time-out values are used on transport-specific application program interfaces (APIs) to terminate the send and/or receive API functions if the expected data is not received in the specified amount of time.|  
|**Send**|Type the number of seconds the HIP runtime should wait for an acknowledgement before it times out. The maximum number of seconds is 3,600; the default is **30** seconds.|  
|**Receive**|Type the number of seconds the host should wait for a response before it times out. The maximum number of seconds is 3,600; the default is **30** seconds.|  
|**Comment**|Type any additional information about the host environment. The comment can be a maximum of 259 alpha-numeric characters.|  
  
> [!CAUTION]
>  The properties of a host environment are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the host environment to function incorrectly.  
  
## See Also  
 [Host Environments Node](../core/host-environments-node.md)   
 [Host Environment Node](../core/host-environment-node.md)   
 [TI Manager Properties](../core/ti-manager-properties.md)