---
title: "Iterative vs. Concurrent TCP-IP Models1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2357589f-84e2-4d32-b01a-9100afe37971
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Iterative vs. Concurrent TCP/IP Models
IBM defines two models for accessing server applications in CICS and IMS. In both models, there is a TCP/IP connection Listener and a Server aspect to the total application. The manner in which the Listener and Server portions of the application are implemented determines whether the model is Iterative or Concurrent.  
  
- Iterative model. In the Iterative model, the Listener and Server portions of the application coexist in the same CICS or IMS TP and run as part of the same CICS task. The server application, therefore, holds the socket until all application processing has completed. This means that after a client TP starts a server TP, another client TP cannot access the Listener or the server TP until the first client is finished.  
  
- Concurrent model. In the Concurrent model, the Listener and Server portions of the application run under the control of different tasks. The Listeners purpose is to accept the connection and invoke the Server task. The Server portion of the application deals with all sending and receiving of application data and performing application-dependent processing. This model allows a higher degree of transaction concurrency because the listening socket is not held by a single client and can instead listen concurrently to multiple clients. Even though the CICS MS Link using TCP/IP programming model is not called concurrent, the server TP does work concurrently instead of iteratively.  
  
  In the four TI-supported TCP/IP models other than IMS Connect, there is both a TCP/IP connection Listener aspect and a Server aspect. The manner in which the Listener and Server portions of the application are implemented determines whether the Iterative or the Concurrent access model is used. The Concurrent access model requires the use of a Transaction Request Message (TRM); the Iterative model does not. The TRM is a formatted data record that identifies the IMS or CICS transaction program (TP) to be invoked and its characteristics.  
  
## In This Section  
 [Iterative Model](../core/iterative-model1.md)  
  
 [Concurrent Model](../core/concurrent-model2.md)  
  
## See Also  
 [Programming Models](../core/programming-models2.md)