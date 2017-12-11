---
title: "TCP-IP Tab (TI Remote Environment Properties)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3723d4f6-3148-4035-9cad-e6f4ee606193
caps.latest.revision: 4
---
# TCP/IP Tab (TI Remote Environment Properties)
Use the TCP/IP tab to set the IP address and port number for the host environment.  
  
|Use this|To do this|  
|--------------|----------------|  
|**IP/DNS address**|Type the address or select from the drop-down list. The address can be a maximum of 256 alphanumeric characters. The drop-down list displays the most recently used IP addresses.|  
|**Port list**|Type the TCP port number. The number can be a maximum of 256 positive numerals separated by semicolons. The port numbers cannot be repeated. The drop-down list displays the most recently used port numbers.|  
|**Time-out in seconds**|The **Send** and **Receive** time-out values are used by the TI runtime environment when it communicates with the host environment. The time-out values are used on transport-specific application program interfaces (APIs) to terminate the send and/or receive API functions if no host acknowledgement is received in the specified amount of time.|  
|**Receive**|Type the number of seconds the host should wait for a response before it times out. The maximum number of seconds is 3,600; the default is **30** seconds.|  
  
> [!CAUTION]
>  The properties of a remote environment are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the remote environment to function incorrectly.  
  
## See Also  
 [Remote Environments Node](../HIS2010/remote-environments-node1.md)   
 [Remote Environment Node](../HIS2010/remote-environment-node2.md)   
 [TI Manager Properties](../HIS2010/ti-manager-properties1.md)