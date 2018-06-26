---
title: "Programming Models2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 021e2e82-f065-45e1-a10a-e540925bcecd
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Programming Models
A programming model defines the method(s) used to access and integrate server applications with host applications. A programming model is a combination of:  
  
- The communication protocol that is used to exchange data with the remote application program.  
  
- The target host environment used to host the server application program.  
  
- The interaction semantics defined by the application to control connect, data exchange, and disconnect sequences.  
  
  Transaction Integrator supports a set of predefined programming models for Windows-initiated processing and for host-initiated processing. The following table summarizes the 11 available WIP programming models depending on the protocol and the target environment.  
  
|Protocol|Target/Host Environment|Host Integration Server Programming Model|Host Integration Server COMTI name|  
|--------------|------------------------------|-----------------------------------------------|----------------------------------------|  
|TCP/IP|CICS|TCP Transaction Request Message (TRM) Link|MS Link|  
|TCP/IP|CICS|TCP Enhanced Listener Message (ELM) Link|n/a|  
|TCP/IP|CICS|TCP Transaction Request Message (TRM) User Data|Concurrent Server|  
|TCP/IP|CICS|TCP Enhanced Listener Message (ELM) User Data|n/a|  
|TCP/IP|IMS|IMS Connect|IMS Open Transaction Management Architecture (OTMA) Connect|  
|TCP/IP|IMS|IMS Implicit|Implicit|  
|TCP/IP|IMS|IMS Explicit|Explicit|  
|TCP/IP|OS/400|OS/400 Distributed Program Calls (DPC)|n/a|  
|LU6.2|CICS|CICS LU6.2 User Data|CICS using LU6.2|  
|LU6.2|CICS|CICS LU6.2 Link|CICS using Link|  
|LU6.2|IMS|IMS LU6.2 User Data|IMS using LU6.2|  
  
 The following table summarizes the five available HIP programming models depending on the protocol and the target environment.  
  
|Protocol|Target/Host Environment|Host Integration Server Programming Model|Host Integration Server COMTI name|  
|--------------|------------------------------|-----------------------------------------------|----------------------------------------|  
|TCP/IP|CICS|TCP Transaction Request Message (TRM) Link|n/a|  
|TCP/IP|CICS|TCP Enhanced Listener Message (ELM) Link|n/a|  
|TCP/IP|CICS|TCP User Data|n/a|  
|TCP/IP|OS/400|OS/400 Distributed Program Calls (DPC)|n/a|  
|LU6.2|CICS|CICS LU6.2 User Data|n/a|  
|LU6.2|CICS|CICS LU6.2 Link|n/a|  
  
## In This Section  
 [TCP Transaction Request Message Link](../core/tcp-transaction-request-message-link2.md)  
  
 [TCP Enhanced Listener Message Link](../core/tcp-enhanced-listener-message-link1.md)  
  
 [TCP Transaction Request Message User Data](../core/tcp-transaction-request-message-user-data2.md)  
  
 [TCP Enhanced Listener Message User Data](../core/tcp-enhanced-listener-message-user-data2.md)  
  
 [IMS Connect](../core/ims-connect1.md)  
  
 [OS/400 Distributed Program Calls](../core/os-400-distributed-program-calls1.md)  
  
 [CICS LU6.2 Link](../core/cics-lu6-2-link1.md)  
  
 [CICS LU6.2 User Data](../core/cics-lu6-2-user-data2.md)  
  
 [IMS LU6.2 User Data](../core/ims-lu6-2-user-data1.md)  
  
 [Choosing the Appropriate Programming Model](../core/choosing-the-appropriate-programming-model1.md)  
  
## See Also  
 [Transaction Integrator Architecture](../core/transaction-integrator-architecture1.md)