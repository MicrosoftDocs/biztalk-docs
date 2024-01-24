---
description: "Learn more about: Communication Models"
title: "Communication Models2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Communication Models
Transaction Integrator (TI) supports the following communication protocols for interacting with the host computer. These protocols are limited to singlerequest/single response. However, the request and response can consist of multiple data segments in the case of unbounded recordsets.  
  
-   **CICS TCP Transaction Request Message Link**  
  
     The host transaction must be designed to be invoked by EXEC CICS LINK.  
  
-   **CICS TCP Transaction Request Message User Data**  
  
     The host transaction must use explicit TCP SEND/RECEIVE.  
  
-   **CICS LU 6.2 Link**  
  
     The host transaction must be IBM DPL-enabled (Distributed Program Link), that is, the mainframe transaction must be designed to be invoked by EXEC CICS LINK.  
  
-   **CICS LU 6.2 User Data**  
  
     The host transaction must use explicit APPC SEND/RECEIVE.  
  
-   **CICS TCP Enhanced  Message Link**  
  
     The host transaction must be IBM DPL-enabled. In other words, the mainframe transaction must be designed to be invoked by EXEC CICS LINK.  
  
-   **CICS TCP Enhanced Message User Data**  
  
     The host transaction must use explicit TCP SEND/RECEIVE.  
  
-   **CICS HTTP Link**  
  
     The host transaction must be designed to be invoked by EXEC CICS LINK.  
  
-   **CICS HTTP User Data**  
  
     The host transaction must use explicit HTTP  SEND/RECEIVE.  
  
-   **IMS Connect**  
  
     Enables you to use TCP/IP with your IMS-based TP without recompiling it. By using IMS Connect or OTMA, you can connect to existing IMS transactions without linking listeners to the TPs.  
  
-   **IMS LU 6.2 User Data**  
  
     The IMS program must use an implicit message queue (the common design model).  
  
-   **IBM System i Distributed Program Calls**  
  
## See Also  
 [Planning for Transaction Integrator](../core/planning-for-transaction-integrator2.md)
