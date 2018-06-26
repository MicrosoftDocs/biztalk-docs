---
title: "Iterative Model1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98198cdc-7b8b-47ef-841f-45138f564d6a
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Iterative Model
In the Iterative model, the Listener and Server portions of the application coexist in the same CICS or IMS TP, so the TP holds the socket until all application processing has been completed. The Iterative model uses this sequence:  
  
1. Create a socket  
  
2. Bind it to a local address  
  
3. Listen (make TCP/IP aware that the socket is available)  
  
4. Select (wait for a connection request)  
  
5. Accept the connection request  
  
6. Read or write the data  
  
7. Close  
  
   **The advantages of the Iterative model are:**  
  
- Simplicity  
  
- Reduced network overhead and delay because a TRM exchange sequence is not required  
  
- Less CPU intensive  
  
- Higher single-threaded transaction throughput  
  
  **The disadvantages of the Iterative model are:**  
  
- Severely limits concurrent access to TPs that run for a long time  
  
- Server application contains all of the SEAPI calls (Create to Close)  
  
- Each TP has its own Listener, which means duplicate code  
  
- Select with timeout causes a CICS region to sleep  
  
## See Also  
 [Iterative vs. Concurrent TCP/IP Models](../core/iterative-vs-concurrent-tcp-ip-models1.md)