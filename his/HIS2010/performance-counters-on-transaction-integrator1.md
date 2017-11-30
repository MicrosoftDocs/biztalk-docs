---
title: "Performance Counters on Transaction Integrator1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c6184e6d-1f85-4cbe-b56b-9d816b07dc02
caps.latest.revision: 4
---
# Performance Counters on Transaction Integrator
The following performance counters are available for Transaction Integrator.  
  
 **Average Method Call Time**  
 This counter measures the average time it takes Transaction Integrator to process method calls made by the client application. The time begins when Transaction Integrator recognizes the request from the client application (the Invoke call). The time ends when Transaction Integrator returns control to the client application. This counter is not specific to any Transaction Integrator programming model. This counter is represented in terms of seconds of elapsed time.  
  
 **Bytes received from host/sec**  
 This counter indicates the number of bytes received from the mainframe by Transaction Integrator. This counter is not specific to any Transaction Integrator programming model. For the CICS Link model, the number reported will be slightly more than the amount of user data due to link model protocol header data. This number is represented in terms of bytes per second.  
  
 **Bytes sent to host/sec**  
 This counter indicates the number of bytes sent from Transaction Integrator to the mainframe. This counter is not specific to any Transaction Integrator programming model. For the CICS Link model, the number reported will be slightly more than the amount of user data due to link model protocol header data. This number is represented in terms of bytes per second.  
  
 **Host response time CICS Link**  
 This counter measures the average time the host spends processing the transaction programs unit of work when the CICS Link model is being used. This average time counter measures the time the host takes to respond to a request sent to it. The time starts after Transaction Integrator sends the final data buffer and ends when the first response buffer is received by Transaction Integrator. This counter is represented in terms of seconds of elapsed time.  
  
 **Host response time CICS Non-link or IMS**  
 This counter measures the average time the host spends processing the transaction programs unit of work when either the CICS Non-link or IMS models are being used. This average time counter measures the time the host takes to respond to a request sent to it. The time starts after Transaction Integrator sends the final data buffer and ends when the first response buffer is received by Transaction Integrator. This counter is represented in terms of seconds of elapsed time.  
  
 **Link calls/sec**  
 This counter measures the number of method calls that use the CICS Link programming model. This number is in terms of calls per second.  
  
 **Non-link calls/sec**  
 This counter measures the number of method calls that use the CICS Non-link or IMS programming model. This number is represented in terms of calls per second.  
  
 **Total calls/sec**  
 This counter indicates the total number of method calls that Transaction Integrator has processed. This counter is not specific to any Transaction Integrator programming model. This number is represented in terms of calls per second.  
  
 **Total errors/sec**  
 This counter indicates the total number of method calls that have returned a non-zero HRESULT indication to the client application. This counter is not specific to any Transaction Integrator programming model. This number is represented in terms of errors per second.  
  
## See Also  
 [Transaction Integrator Performance Guide](../HIS2010/transaction-integrator-performance-guide2.md)   
 [System Monitor](../HIS2010/system-monitor2.md)