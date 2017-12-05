---
title: "Network Tab (Host Environment Properties)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15332"
ms.assetid: a18e5d62-b149-4b91-bc8e-d349ba4a837e
caps.latest.revision: 4
---
# Network Tab (Host Environment Properties)
The **Network** tab defines the network characteristics that the host uses to interact with the Windows environment and to ensure that unauthorized requests are not inadvertently processed.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Network type**|Select the type of network used to communicate with the host environment. The choices are:<br /><br /> -   TCP/IP (default)<br />-   SNA|  
|**Remote endpoint manager**|For a TCP/IP network, select or type the IP address of the host or the host name registered in the DNS. For an SNA network, type the LU name associated with the host system. In either case, the name can be a maximum of 259 alpha-numeric characters.|  
  
> [!CAUTION]
>  The properties of a host environment are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the host environment to function incorrectly.  
  
## See Also  
 [Host Environments Node](../HIS2010/host-environments-node2.md)   
 [Host Environment Node](../HIS2010/host-environment-node2.md)   
 [TI Manager Properties](../HIS2010/ti-manager-properties1.md)