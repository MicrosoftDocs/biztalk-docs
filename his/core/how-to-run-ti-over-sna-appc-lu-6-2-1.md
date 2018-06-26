---
title: "How to Run TI over SNA (APPC-LU 6.2)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c746f4b4-fd8f-4420-9587-d54a0986176d
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Run TI over SNA (APPC/LU 6.2)
If you have a distributed network, use Transaction Integrator (TI) over an SNA (APPC/LU 6.2) network connection to take advantage of its support for two-phase commit (2PC) in ACID (atomic, consistent, isolated, and durable) transaction processing. To support ACID transactions, your COBOL transaction program (TP) must support Sync Level 2. The TCP/IP protocol has no default support for 2PC, so TCP/IP is not appropriate in a distributed network.  
  
### To run a TI application over an SNA network  
  
1. Configure the mainframe (CICS or IMS) for SNA, and establish a connection with your Windows-based [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer.  
  
2. Install the COBOL transaction programs within the CICS or IMS region that receives TI-initiated calls.  
  
3. Define an appropriate SNA remote environment for the CICS or IMS region that receives TI-initiated calls.  
  
4. Build the TI component with a method for each transaction in the TP.  
  
5. Deploy the TI component in a COM+ application to create a TI Automation server.  
  
   Run the client application that calls the new TI Automation server to automate the TP.  
  
## See Also  
 [How to Run TI Over TCP/IP](../core/how-to-run-ti-over-tcp-ip2.md)   
 [Windows-Initiated Processing Overview](../core/windows-initiated-processing-overview2.md)