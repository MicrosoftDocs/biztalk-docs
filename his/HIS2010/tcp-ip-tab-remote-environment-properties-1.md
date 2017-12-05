---
title: "TCP-IP Tab (Remote Environment Properties)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15213"
ms.assetid: 756b3db4-e247-4aee-906b-21b476f792b4
caps.latest.revision: 4
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
 [Remote Environments Node](../HIS2010/remote-environments-node1.md)   
 [Remote Environment Node](../HIS2010/remote-environment-node2.md)   
 [CICS Tab (for TCP/IP Properties)](../HIS2010/cics-tab-for-tcp-ip-properties-1.md)   
 [TI Manager Properties](../HIS2010/ti-manager-properties1.md)