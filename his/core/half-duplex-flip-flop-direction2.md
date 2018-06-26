---
title: "Half-Duplex Flip-Flop Direction2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d5bba82-4006-47f2-8e16-081f9615de1c
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Half-Duplex Flip-Flop Direction
The **BIND** used to establish the session carries information about the initial state of the bracket and direction machines. This can be specified in the **BIND** if either of the following conditions are satisfied:  
  
- Brackets are not used.  
  
- Brackets reset state is in-bracket.  
  
  If neither of the conditions hold, the initial direction state is contention.  
  
  When the direction is specified in the **BIND**, the application should assume the direction state specified in the half-duplex reset state as soon as data can flow. This field can be obtained indirectly by using a **BIND** check index that only accepts a particular direction, or directly by reading the **HDXRSET** field in the bind information control block (BICB) on the [Open(PLU) OK Confirm](./open-plu-oconfirm1.md) message or by reading the **BIND** on the [Open(PLU) Request](./open-plu-request2.md). For more information about opening the PLU connection, see [Opening the PLU Connection](../core/opening-the-plu-connection1.md).  
  
  When in contention state, either the PLU or the application can initiate a bracket. (For more information, see [Brackets](../core/brackets1.md).) The successful initiator of the bracket obtains direction unless direction is relinquished when opening the bracket by sending Begin Bracket (BB), Begin Chain (BC), End Chain (EC), or Change Direction (CD). Because the secondary is assumed to be the contention winner, the application can assume send state from contention sending BB and rejecting any subsequent **Status-Control(BID) Request** from the local node before receiving **Status-Session(BETB)**. When the application accepts a S**tatus-Control(BID) Request** in contention state, it must assume receive state.  
  
  Half-duplex flip-flop direction can change through the following actions:  
  
- Sending or receiving data with the change direction (CD) indicator in the RH, and the corresponding change direction indicator (CDI) flag on the **DATAFMI** and [Status-Control](./status-control1.md) messages. Note that CD is only used at the end of a chain (and for applications receiving segments that will be delivered with ECI, EBIUI). Also note that CD is valid on the following normal flow **Status-Control** requests: **LUSTAT**, **CANCEL**, **CHASE** and **QC**.  
  
- Receiving a negative response when the application should assume receive state (error recovery pending state). For more information, see [Recovery](../core/recovery1.md).  
  
- If the application rejects data from the host carrying CDI, it must remain in receive state.  
  
  Providing the FM profile is correct (3, 4, or 7), the application can request direction from the host using a **Status Control(SIGNAL) Request** with CODE1 set to 0x0001. CODE2 is set to a user-defined value.  
  
  The following three figures illustrate the direction protocol for applications using the half-duplex flip-flop mode.  
  
  In the first figure, the application issues and receives the CD without error.  
  
  ![](../core/media/his-32703m.gif "his_32703m")  
  Application issues and receives the CD without error  
  
  In the following figure, the host sends a negative response to inbound data. The application assumes receive state, and then the host sends CD to give the application direction.  
  
  ![](../core/media/his-32703ma.gif "his_32703ma")  
  Host sends negative response to inbound data  
  
  In the following figure, a complete outbound chain is received without error, but is rejected by the application. Note that even though the chain carried CD, the application does not have direction.  
  
  ![](../core/media/his-32703mb.gif "his_32703mb")  
  Complete outbound chain received without error, but is rejected by application  
  
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