---
title: "Programming Models1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0438a2f3-93d4-451c-a952-66e8cec9ee67
caps.latest.revision: 5
---
# Programming Models
A programming model defines the method(s) used to access and integrate server applications with host applications. A programming model is a combination of:  
  
-   The communication protocol that is used to exchange data with the remote application program.  
  
-   The target host environment used to host the server application program.  
  
-   The interaction semantics defined by the application to control connect, data exchange, and disconnect sequences.  
  
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
 [TCP Transaction Request Message Link](../HIS2010/tcp-transaction-request-message-link1.md)  
  
 [TCP Enhanced Listener Message Link](../HIS2010/tcp-enhanced-listener-message-link2.md)  
  
 [TCP Transaction Request Message User Data](../HIS2010/tcp-transaction-request-message-user-data1.md)  
  
 [TCP Enhanced Listener Message User Data](../HIS2010/tcp-enhanced-listener-message-user-data1.md)  
  
 [IMS Connect](../HIS2010/ims-connect2.md)  
  
 [OS/400 Distributed Program Calls](../HIS2010/os-400-distributed-program-calls2.md)  
  
 [CICS LU6.2 Link](../HIS2010/cics-lu6-2-link2.md)  
  
 [CICS LU6.2 User Data](../HIS2010/cics-lu6-2-user-data1.md)  
  
 [IMS LU6.2 User Data](../HIS2010/ims-lu6-2-user-data2.md)  
  
 [Choosing the Appropriate Programming Model](../HIS2010/choosing-the-appropriate-programming-model2.md)  
  
## See Also  
 [Transaction Integrator Architecture](../HIS2010/transaction-integrator-architecture2.md)