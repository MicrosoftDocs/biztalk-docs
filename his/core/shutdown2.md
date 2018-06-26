---
title: "Shutdown2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 284ea4a8-d59d-45a0-bb47-cc2ac0d7d25b
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Shutdown
The shutdown protocol provides a means for the host application to stop the application from sending any further normal flow requests. This protocol is used when the host application wants to end the session in an orderly manner and is only available for sessions using function management (FM) profile 3 or 4.  
  
 If the local node receives a **SHUTD** request from the host, it issues a **Status-Control(SHUTD) Request** (without **ACKRQD**) to request the application to enter a quiesced state at a convenient time. The application determines what is convenient. For example, it could be after a **Status-Session(BETB)** has been received.  
  
 When the application decides it is ready to quiesce, it should issue a **Status-Control(SHUTC) Request** (again without **ACKRQD**) to indicate this transition. The local node will notify the host of this change by sending a **SHUTC** request. The host can continue sending normal flow outbound requests and can subsequently take one of the following actions:  
  
- The host terminates the primary logical unit (PLU) session by sending an **UNBIND** request. The local node closes the PLU connection by sending a [Close(PLU) Request](./close-plu-request2.md) to the application. The system services control point (SSCP) session remains active.  
  
- The host abandons the shutdown procedure by sending an **RELQ** request. The local node sends a **Status-Control(RELQ) Request** (with **ACKRQD**) to the application to indicate that it can now resume sending on the PLU session. **RELQ** is only supported on sessions using FM profile 4.  
  
- The host resets the session by sending **CLEAR**, a Transmission Service profile (TS profile) 3 or 4. One of the effects of this is to release the quiesced state. (For more information, see [Recovery](../core/recovery1.md).)  
  
  The following two figures illustrate the shutdown protocols between the local node and the application and how those protocols relate to the underlying SNA protocols.  
  
  In the following figure, the host sends **SHUTD** while the application is sending in the in-bracket state. The application completes the bracket, sends **Status-Control(SHUTC) Request**, and the host terminates the PLU session by sending **UNBIND**. The local node closes the PLU connection.  
  
  ![](../core/media/32703r.gif "32703r")  
  Host sends SHUTD while the application is sending in the in-bracket state  
  
  In the following figure, the host sends **SHUTD** while the application is sending in the in-bracket state. The application completes the bracket, sends **Status-Control(SHUTC) Request**, and then the host releases the application from the quiesced state by sending **RELQ**. The local node sends a **Status-Control(RELQ) Request** to the application, which initiates a new bracket.  
  
  ![](../core/media/32703ra.gif "32703ra")  
  Host sends SHUTD while the application is sending in the in-bracket state  
  
## See Also  
 [Opening the PLU Connection](../core/opening-the-plu-connection1.md)   
 [PLU Session](../core/plu-session2.md)   
 [Outbound Chaining](../core/outbound-chaining2.md)   
 [Inbound Chaining](../core/inbound-chaining1.md)   
 [Segment Delivery](../core/segment-delivery1.md)   
 [Brackets](../core/brackets1.md)   
 [Direction](../core/direction1.md)   
 [Pacing and Chunking](../core/pacing-and-chunking1.md)   
 [Confirmation and Rejection of Data\]](../core/confirmation-and-rejection-of-data]1.md)   
 [Shutdown and Quiesce](../core/shutdown-and-quiesce1.md)   
 [Recovery](../core/recovery1.md)   
 [Application-Initiated Termination](../core/application-initiated-termination1.md)   
 [LUSTATs\]](../core/lustats]1.md)   
 [Response Time Monitor Data](../core/response-time-monitor-data1.md)