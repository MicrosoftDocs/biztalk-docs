---
title: "Concurrent Model2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0157ebd0-6151-4a9d-83ba-1d836e84847f
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Concurrent Model
In the Concurrent model, the Listener and Server portions of the TP run under the control of different tasks. The Listener's sole purpose is to accept the connection and spawn the Server task. The Server portion of the application sends and receives data and performs TP-dependent processing. This model allows a higher degree of concurrency because the listening socket is not held for an extended period of time.  
  
 The Listener must receive a TRM as the first data from the TI run-time environment. The TRM tells the Listener which TP to invoke and the characteristics of that program. After sending the TRM, the TI run-time environment must wait for a response before sending data. The Listener of the Concurrent model follows this sequence:  
  
1. Create a Listening socket  
  
2. Bind it to a local address  
  
3. Listen (make TCP/IP aware that the socket is available)  
  
4. Select (wait for a connection request)  
  
5. Accept the connection  
  
6. Read the TRM  
  
7. Check the validity of the requested transaction ID (TRANID)  
  
8. Give a socket (prepare TCP/IP for the transfer of the socket)  
  
9. Start the task  
  
10. Synchronize on the worker task acceptance of the socket  
  
11. Select (wait for connection request)  
  
    **The Worker task of the Concurrent model follows this procedure:**  
  
12. Take a socket (accept the socket request from the Listener).  
  
13. Write a response to the TRM.  
  
14. Read or write application data.  
  
15. Close.  
  
    **The advantages of the Concurrent model are:**  
  
- Easy to implement concurrent access to TPs that run for a long time.  
  
- One Listener is shared by many TPs.  
  
- Server TCP/IP logic is simple.  
  
  **The disadvantages of the Concurrent model are:**  
  
- Increased network overhead and delays due to the requirement of the TRM exchange.  
  
- More CPU and resource intensive than is the Iterative model.  
  
## See Also  
 [Iterative vs. Concurrent TCP/IP Models](../core/iterative-vs-concurrent-tcp-ip-models1.md)