---
title: "Performance Monitoring Counters2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56c5abf3-922c-4dfc-aed7-a27b0a3a415f
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Performance Monitoring Counters
Transaction Integrator (TI) has 24 basic performance monitoring counters that you can add to the Windows System Monitor to analyze performance and find out where the bottlenecks are in your system. You can select any of the counters, and then click **Explain** to get information about that counter.  
  
 The 24 TI performance monitoring counters are as follows:  
  
- **Active Clients**  
  
   Displays the total number of active clients, which are those clients that have created an instance of a TI object but have not yet released that instance.  
  
- **Average method call time**  
  
   Measures the average number of seconds of elapsed time that TI uses to process method calls made by the client application. The time begins when TI receives the request from the client application (the `Invoke` call). The time ends when TI returns control to the client application. This counter includes the host response time, and it is not specific to any TI programming model. Consider the following two facts when you are using this counter:  
  
  -   Special TI properties, such as `GetNewRecordsSet`, have been omitted from the calculation.  
  
  -   Two-phase commit (2PC) response time is not considered and is omitted from the calculation.  
  
  > [!NOTE]
  >  Host response times for CICS, CICS Non-LINK, and IMS can be subtracted from the average method call time to calculate the amount of time TI spends processing methods. For example, assume a transaction takes one minute to complete. The host response time is 48 seconds and the average method call time is 60 seconds. Subtracting the host response time from the average method call time leaves 12 seconds that TI uses to process the methods. The host uses most of the transaction time.  
  
- **Bytes recv'd from a TCP host / sec**  
  
   Displays the number of bytes per second received from the mainframe by TI over the TCP/IP protocol. This counter is not specific to any TI TCP/IP programming model. For the CICS MSLink model, the number reported will be slightly more than the amount of user data due to the Link model protocol header data. Bytes received from the host represent all data traffic, including user data.  
  
- **Bytes recv'd from an SNA host / sec**  
  
   Displays the number of bytes per second received from the mainframe by TI over the SNA protocol (APPC/LU 6.2). This counter is not specific to any TI SNA (APPC/LU 6.2) programming model. For the CICS Link model, the number reported will be slightly more than the amount of user data due to Link model protocol header data. Bytes received from the host represents all data traffic, including user data and two-phase commit (2PC) flows.  
  
- **Bytes sent to a TCP host / sec**  
  
   Displays the number of bytes per second sent from TI to the mainframe over the TCP/IP protocol. This counter is not specific to any TI TCP programming model. For the CICS MS Link model, the number reported will be slightly more than the amount of user data due to Link model protocol header data. Bytes sent to the host represent all data traffic over TCP/IP, including user data.  
  
  > [!NOTE]
  >  To determine the TI load on the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer, you can compare the average number of bytes sent and received by TI with the corresponding performance counters for Host Integration Server. For example, if the average number of bytes sent to the host from TI is 20 and the average number of bytes sent to the host by Host Integration Server is 100, Host Integration Server traffic is responsible for most of the load. Consequently, the amount of information coming back from the host could be less than that going to the host. That is why two counters are available, one for the number of bytes sent and one for the number of bytes received.  
  
- **Bytes sent to an SNA host / sec**  
  
   Displays the number of bytes per second sent from TI to the mainframe over the SNA (APPC/LU 6.2) protocol. This counter is not specific to any TI SNA (APPC/LU 6.2) programming model. For the CICS Link model, the number reported will be slightly more than the amount of user data due to Link model protocol header data. This number is represented in terms of bytes per second.  
  
- **Calls currently executing**  
  
   Displays the number of method calls that are currently being executed.  
  
- **Cumulative calls**  
  
   Displays the total number of method calls that have occurred since the COM+ application was started.  
  
- **Host resp time CICS Link**  
  
   Measures the average time the host spends processing the transaction program's unit of work when the CICS Link model is in use. In other words, this counter measures how long the host takes to respond to a request. The time starts after TI sends the final data buffer and ends when the first response buffer is received by TI. This counter is represented in terms of seconds of elapsed time. Consider the following two facts when you are using this counter:  
  
  -   Two-phase commit (2PC) response time is not considered and is omitted from the calculation.  
  
  -   Multiple receives might be contained in the first response buffer sent to TI. Therefore, the response time ends when TI has obtained all receives to the first response buffer.  
  
- **Host resp time CICS Non-link or IMS**  
  
   Measures the average time the host spends processing the transaction program's unit of work when either the CICS Non-LINK or IMS models is in use. In other words, this counter measures how long the host takes to respond to a request. The time starts after TI sends the final data buffer and ends when the first response buffer is received by TI. This counter is represented in terms of seconds of elapsed time. Consider the following two facts when you are using this counter:  
  
  -   Two-phase commit (2PC) response time is not considered and is omitted from the calculation.  
  
  -   Multiple receives might be contained in the first response buffer sent to TI. Therefore, the response time ends when TI has obtained all receives to the first response buffer.  
  
- **Host resp time TCP Concurrent Server**  
  
   Measures the average time the host spends processing the transaction programs unit of work when the TCP/IP CICS Concurrent Server model is being used. This average time counter measures the time the host takes to respond to a request sent to it. The time starts after TI sends the final data buffer and ends when the first response buffer is received by TI. This counter is represented in terms of seconds of elapsed time.  
  
- **Host resp time TCP MS Link**  
  
   Measures the average time the host spends processing the transaction programs unit of work when the TCP/IP CICS MSLink model is being used. This average time counter measures the time the host takes to respond to a request sent to it. The time starts after TI sends the final data buffer and ends when the first response buffer is received by TI. This counter is represented in terms of seconds of elapsed time.  
  
- **Host resp time TCP IMS Connect or OTMA**  
  
   Measures the average time the host spends processing the transaction programs unit of work when the TCP/IP IMS Explicit model is being used. This average time counter measures the time the host takes to respond to a request sent to it. The time starts after TI sends the final data buffer and ends when the first response buffer is received by TI. This counter is represented in terms of seconds of elapsed time. IMS Connect or OTMA enables customers to connect to existing IMS transactions without linking listeners to the transaction programs (TP), so you do not have to recompile your IMS TP.  
  
- **Link calls / sec**  
  
   Displays the number of method calls that use the CICS LINK programming model. This number represents of calls per second.  
  
- **Non-link calls / sec**  
  
   Displays the number of method calls that use the CICS Non-LINK or IMS programming model. This number represents calls per second.  
  
- **TCP Concurrent Server calls / sec**  
  
   Displays the number of method calls that use the TCP/IP CICS Concurrent Server programming model. This number represents calls per second.  
  
- **TCP MSLink calls / sec**  
  
   Displays the number of method calls per second that use the TCP/IP CICS MS Link programming model.  
  
- **TCP OTMA calls / sec**  
  
   Displays the number of method calls that use the TCP/IP OTMA programming model. This number represents calls per second.  
  
- **Total calls / sec**  
  
   Displays the total number of method calls per second that TI has processed. This counter is not specific to any TI programming model.  
  
- **Total errors / sec**  
  
   Displays the total number of method calls per second that have returned a non-zero HRESULT to the client application. This counter is not specific to any TI programming model.  
  
  > [!NOTE]
  >  Comparing method call errors with CICS LINK calls and CICS Non-LINK calls shows the severity of a given situation. For example, if the Method call errors counter reports two errors per second and LINK calls or CICS Non-LINK calls are reporting 50 method calls per second, it may indicate that one client application has trouble with a specific host application. Consequently, if the Method call errors counter reports 50 errors per second and CICS LINK calls or CICS Non-LINK calls are reporting 50 method calls per second, this indicates that a connection to the host might have been terminated.  
  
## In This Section  
 [Method Calls per Second](../core/method-calls-per-second2.md)  
  
 [Average Method Call Time](../core/average-method-call-time2.md)  
  
 [Errors Per Second](../core/errors-per-second2.md)  
  
 [Host Response Time](../core/host-response-time2.md)  
  
 [Bytes Sent Per Second](../core/bytes-sent-per-second2.md)  
  
 [Bytes Received Per Second](../core/bytes-received-per-second1.md)