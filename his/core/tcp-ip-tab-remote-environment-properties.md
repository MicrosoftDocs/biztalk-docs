---
title: "TCP-IP Tab (Remote Environment Properties)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15211"
ms.assetid: 1ddfe1c5-3acc-4d85-bb6e-4d6812aa6ef4
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
robots: noindex,nofollow
---
# TCP/IP Tab (Remote Environment Properties)
Use the **TCP/IP** tab to define the network characteristics that the Windows environment uses to interact with the host.  
  
|Use this|To do this|  
|--------------|----------------|  
|**IP/DNS Address**|Type the address or select one from the drop-down list. The address can be a maximum of 256 alphanumeric characters. The drop-down list displays the most recently used IP addresses.|  
|**TCP ports list**|Type the TCP port number. The number can be a maximum of 256 positive numerals separated by semicolons. The port numbers cannot be repeated. The drop-down list displays the most recently used port numbers.|  
|**Time-out if no response within** <br /> ***number* seconds**|Type the number of seconds. The send and receive time-out values are used by the WIP runtime environment when it communicates with the host environment. The time-out values are used on transport-specific APIs to terminate the receive API function when no host data or acknowledgement is received in the specified amount of time. The number of seconds can be a maximum of 3600 and a minimum of 0.|  
  
> [!CAUTION]
>  The properties of a remote environment are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the remote environment to function incorrectly.  
  
## See Also  
 [Remote Environments Node](../core/remote-environments-node.md)   
 [Remote Environment Node](../core/remote-environment-node.md)   
 [CICS Tab (for TCP/IP Properties)](../core/cics-tab-for-tcp-ip-properties.md)   
 [TI Manager Properties](../core/ti-manager-properties.md)