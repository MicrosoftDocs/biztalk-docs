---
title: "Using Ports in Orchestrations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "send ports, receiving"
  - "ports, configuring manually"
  - "send ports, messages"
  - "ports, creating"
  - "ports, messages"
  - "creating, ports"
  - "send ports, sending"
  - "ports, operations"
  - "configuring, ports"
  - "ports, deleting"
  - "deleting, ports"
  - "orchestrations, ports"
  - "Port Configuration Wizard [Orchestration Designer]"
  - "ports"
  - "ports, about ports"
  - "ports, configuring"
ms.assetid: 968b2d1b-e233-4eb0-8254-9ec6b7642cdf
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Ports in Orchestrations
Ports specify how your orchestration will send messages to and receive messages from other business processes. Each port has a type, a direction, and a binding, which together determine the direction of communication, the pattern of communication, the location to or from which the message is sent or received, and how the communication takes place.  
  
> [!NOTE]
>  There is a distinction between a port and a port type. A port is an instance of a port type; several different ports may have the same port type.  
  
 Depending on these factors, a port may have associated with it a URI (a physical location), a transport (either FILE, HTTP, SOAP, SMTP or BizTalk Message Queuing), a send pipeline to prepare a message for sending (for example, by assembling, encrypting, compressing, or performing some other action on it), and a receive pipeline to prepare a received message for processing (for example, by disassembling, decrypting, or decompressing it).  
  
 You add ports to an orchestration in much the same way that you add controls to a Web Form or Windows Form. You can also add ports by using the Orchestration View window.  
  
## In This Section  
  
-   [Communication Pattern](../core/communication-pattern.md)  
  
-   [Communication Direction](../core/communication-direction.md)  
  
-   [Port Bindings](../core/port-bindings.md)  
  
-   [How to Use Ports in Orchestrations](../core/how-to-use-ports-in-orchestrations.md)  
  
-   [How to Work with Port Types](../core/how-to-work-with-port-types.md)  
  
-   [How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md)  
  
-   [Working with Direct Bound Ports in Orchestrations](../core/working-with-direct-bound-ports-in-orchestrations.md)  
  
## See Also  
 [How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md)   
 [Using Role Links in Orchestrations](../core/using-role-links-in-orchestrations.md)