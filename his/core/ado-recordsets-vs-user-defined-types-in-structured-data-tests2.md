---
description: "Learn more about: ADO Recordsets vs. User-Defined Types in Structured Data Tests"
title: "ADO Recordsets vs. User-Defined Types in Structured Data Tests2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# ADO Recordsets vs. User-Defined Types in Structured Data Tests
Tests on structured data transfer show that user-defined types outperformed ADO recordsets in CPU usage, transactions per second, and response time.  
  
 Tests were conducted using six Pentium 300 MHz clients, one quad-processor Xeon p2-400 system as a gateway, and four SNA host server computers to emulate the CICS region of a mainframe. When transferring user-defined types, the clients were under less stress, and there was much better throughput overall. User-defined types were also much less stressful to the server.  
  
 The overall response times for the user-defined types are also much less because of the metadata that recordsets contain. The metadata inside the recordsets increases the size of the data marshaled back and forth across the DCOM connection. In addition to the increased size, the metadata increases processing overhead.  
  
## See Also  
 [Transaction Integrator Performance Guide](../core/transaction-integrator-performance-guide1.md)
