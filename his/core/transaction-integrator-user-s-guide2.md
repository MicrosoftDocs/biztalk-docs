---
title: "Transaction Integrator User&#39;s Guide2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 69933b5c-2184-4654-b1e1-6f951462a703
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Transaction Integrator User&#39;s Guide
This section contains information about using Transaction Integrator (TI). Transaction Integrator is the synchronous .NET Framework application integration solution in [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)]. TI enables you to integrate mainframe-based transaction programs (TP) and AS/400 transactions with component-based Windows Server System applications when the following conditions are true:  
  
- A synchronous or transactional solution is needed.  
  
- Both the client and server systems are running at the time the call is made.  
  
  If you need an application integration solution that does not require the client and server systems to be running at the time the call is made, use an asynchronous messaging solution such as Message Integrator (WCF Channel for WebSphere MQ) instead of TI. In an asynchronous solution, the middle-tier queuing system is running at the time the client issues a request message, the server retrieves the message and sends back the reply, and then the client receives the reply back from the middle tier.  
  
  With TI, you can integrate existing mainframe-based TPs with Windows-based applications built on the .NET Framework. You might not even have to modify your TP if you have separated the business logic from the presentation logic. The wizards in TI guide you through the modification process, step by step.  
  
  With TI, you can preserve existing CICS and IMS TPs as you move to a three-tier client/server or Web-to-host computing environment. By using TI to invoke mainframe transactions, you can program in the visual object-oriented environments and programming languages that you know while you maintain access to host transactions.  
  
  TI supports both SNA connectivity and TCP/IP connectivity without requiring a host footprint or costly host transaction rewrites. You can choose SNA connectivity if you need two-phase commit (2PC), or choose TCP/IP connectivity if you need direct throughput. IBM has not implemented 2PC for the TCP/IP protocol, but for those cases where 2PC is not necessary, TCP/IP can give you direct connectivity.  
  
  True integration of online transaction processing (OLTP) with .NET-compliant systems means the integration of CICS and IMS with Windows-based solutions. CICS and IMS are widely used in the mainframe arena to create distributed OLTP solutions such as customer tracking and order entry. TI integrates CICS and IMS with .NET by creating .NET interfaces to the CICS and IMS transactions and then running the CICS and IMS transactions on the mainframe from Windows.  
  
  A TI object in a .NET application works in concert with the TI run-time environment, Microsoft Distributed Transaction Coordinator (MS DTC), and the associated remote environment (RE) to drive a CICS or IMS TP. Together, they accomplish these tasks:  
  
- Activate the host (mainframe) TP.  
  
- Pass the parameters specified by the TI object to the TP.  
  
- Run the TP.  
  
- Return the results to the TI object.  
  
  When you reference a TI object (an assembly .dll file) in a .NET application, that application automatically starts the TI run-time environment and uses the endpoint information associated remote environment to invoke the mainframe transaction that is associated with that TI method.  
  
## In This Section  
 [Getting Started with TI](../core/getting-started-with-ti1.md)  
  
 [Windows-Initiated Processing Overview](../core/windows-initiated-processing-overview2.md)  
  
 [Working with Host-Initiated Processing](../core/working-with-host-initiated-processing1.md)  
  
 [Transaction Integrator Performance Guide](../core/transaction-integrator-performance-guide1.md)