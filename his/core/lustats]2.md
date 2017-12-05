---
title: "LUSTATs]2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 79ecb061-c33b-4ca1-920c-586d1d879e7e
caps.latest.revision: 3
---
# LUSTATs]
The data flow control (DFC) logical unit status **LUSTAT** message is used within SNA to convey four bytes of sense data to the other session partner. It can also be used simply to send a response header (RH) to the other session partner (for example, to open a bracket). (For more information, see the figures in [Bracket Initiation](../core/bracket-initiation2.md).) The message flows on the normal flow and so is subject to direction restrictions. However, it can be sent without end bracket (EB) or change direction (CD) on a half-duplex flip-flop session that is in error recovery pending state. (For more information, see [Recovery](../core/recovery2.md).)  
  
 The local node allows the application to send **Status-Control(LUSTAT) Request** messages at any time that data traffic is active, except while sending data in chain. If the application is in a receiving state (using half-duplex protocol), the **LUSTAT** is queued up and used to provide the sense codes, which are filled into the next outbound request, and the SDI flag is set. The application can therefore present the sense codes for an error state without waiting for the next outbound data if required.  
  
 The first byte of sense data must be 0x08 to generate a **DATAFMI** message with **SDI** (to be converted to a negative response). Other **LUSTATs** are left queued on the session until they can be sent.  
  
 If multiple **Status-Control(LUSTAT)** messages are sent by the application while in a receive state, the local node queues them all. When outbound data has been delivered to the application with **SDI** set, as indicated earlier, and the application has converted it to a [Status-Acknowledge(Ack)](../core/status-acknowledge-ack-1.md), the local node sends the negative response and the remaining **LUSTATs** (which can now flow because the half-duplex flip-flop state is error recovery pending).  
  
 If the application intends to send multiple **Status-Control(LUSTAT)** messages to the host, it is possible that the host will attempt to initiate recovery before the last **LUSTAT** has been sent. In this case, the error recovery chain will be rejected by the next **LUSTAT**.  
  
 Note that the application can send **Status-Control(LUSTAT) Request** with or without **ACKRQD**. The local node will map these to **RQD** and **RQE LUSTATs** respectively.  
  
 The following three figures illustrate the use of **Status-Control(LUSTAT)** messages by an application using the half-duplex flip-flop mode.  
  
 In the first figure, the application issues **Status-Control(LUSTAT)** when it has direction.  
  
 ![](../core/media/32703v.gif "32703v")  
Application issues Status-Control(LUSTAT) when it has direction  
  
 In the following figure, the application sends **Status-Control(LUSTAT)** request when receiving data between chain. Next, outbound data is delivered with **SDI** set, which gets converted to negative **RSP**.  
  
 ![](../core/media/32703va.gif "32703va")  
Application issues Status-Control(LUSTAT) request when receiving data between chain  
  
 In the following figure, the application sends several **Status-Control(LUSTAT)** requests when receiving data in chain. Next, outbound data is delivered with **SDI** set which gets converted to negative response. Subsequent **LUSTATs** are sent to host.  
  
 ![](../core/media/32703vb.gif "32703vb")  
Application sends several Status-Control(LUSTAT) requests when receiving data in chain  
  
## See Also  
 [Opening the PLU Connection](../core/opening-the-plu-connection2.md)   
 [Closing the PLU Connection](../core/closing-the-plu-connection2.md)   
 [PLU Session](../core/plu-session1.md)   
 [Outbound Chaining](../core/outbound-chaining1.md)   
 [Inbound Chaining](../core/inbound-chaining2.md)   
 [Segment Delivery](../core/segment-delivery2.md)   
 [Brackets](../core/brackets2.md)   
 [Direction](../core/direction2.md)   
 [Pacing and Chunking](../core/pacing-and-chunking2.md)   
 [Confirmation and Rejection of Data\]](../core/confirmation-and-rejection-of-data]2.md)   
 [Shutdown and Quiesce](../core/shutdown-and-quiesce2.md)   
 [Recovery](../core/recovery2.md)   
 [Application-Initiated Termination](../core/application-initiated-termination2.md)   
 [Response Time Monitor Data](../core/response-time-monitor-data2.md)