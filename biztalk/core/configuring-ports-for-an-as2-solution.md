---
description: "Learn more about: Configuring Ports for an AS2 Solution"
title: "Configuring Ports for an AS2 Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 715358b1-4226-476b-b0de-2b91434aa24c
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Ports for an AS2 Solution
You can use the following receive and send ports to transmit EDI and non-EDI messages over AS2:  
  
 **Receive Ports**  
  
|To Receive|To Send|Type of Port|  
|----------------|-------------|------------------|  
|An EDI or non-EDI message or acknowledgment|An MDN response (if in synchronous mode) or an HTTP response (if in asynchronous mode)|Two-way request-response HTTP receive port|  
|An MDN response|-|One-way HTTP receive port|  
  
 **Send Ports**  
  
|To Send|To Receive|Type of Port|  
|-------------|----------------|------------------|  
|An EDI or non-EDI message or acknowledgment<br /><br /> (agreement-based routing)|-|Static one-way HTTP send port|  
|An EDI or non-EDI message or acknowledgment<br /><br /> (content-based routing)|An MDN response|Dynamic two-way solicit-response HTTP send port|  
|An EDI or non-EDI message or acknowledgment<br /><br /> (content-based routing)|-|Dynamic one-way HTTP send port|  
|An asynchronous MDN response<br /><br /> (content-based routing)|-|Dynamic one-way send port|  
|An asynchronous MDN response|-|Static one-way send port|  
  
## In This Section  
  
-   [Configuring a Receive Port for Messages over AS2](../core/configuring-a-receive-port-for-messages-over-as2.md)  
  
-   [Configuring a Receive Port for Incoming MDNs](../core/configuring-a-receive-port-for-incoming-mdns.md)  
  
-   [Configuring a Static Send Port for Messages over AS2](../core/configuring-a-static-send-port-for-messages-over-as2.md)  
  
-   [Configuring a Dynamic Send Port for Messages over AS2](../core/configuring-a-dynamic-send-port-for-messages-over-as2.md)  
  
-   [Configuring a Static Send Port for Asynchronous MDNs over AS2](../core/configuring-a-static-send-port-for-asynchronous-mdns-over-as2.md)  
  
-   [Configuring a Dynamic Send Port for Asynchronous MDNs over AS2](../core/configuring-a-dynamic-send-port-for-asynchronous-mdns-over-as2.md)  
  
## See Also  
 [Developing and Configuring BizTalk Server AS2 Solutions](../core/developing-and-configuring-biztalk-server-as2-solutions.md)
