---
title: "PLU Session Characteristics2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 49b5f7d2-8cfc-43d2-9379-c6e30349eb88
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# PLU Session Characteristics
The local node provides support on the primary logical unit (PLU) session for function management (FM) profiles 2, 3, 4, and 7 and Transmission Service profiles (TS profiles) 2, 3, 4, and 7. Support of these profiles means that the local node supports LU-LU session types 0, 1, 2, and 3. Using the PLU connection, the application can send and receive any FM data that is valid for these LU-LU types.  
  
 The protocols appropriate to a particular session are determined by the parameters in the **BIND** request that establishes the session. The **BIND** parameters are reported to the application in the bind information control block (BICB) on the [Open(PLU) OK Confirm](./open-plu-oconfirm1.md) message. It is the application's responsibility to conform to the session protocols reported in the BICB.  
  
 Due to the wide range of **BIND** parameters allowable on a session and the options available to an application in the CICB on the [Open(PLU) OK Response](./open-plu-oresponse2.md), this section does not attempt a complete description of the protocols for a particular session. The remaining topics in this section describe the general protocol characteristics of the PLU session, such as chaining, brackets, and so on.  
  
 Most of the protocol descriptions in the remainder of this section are accompanied by figures to illustrate the important features. The figures show:  
  
- The relevant response header flags in SNA requests/responses.  
  
- The sequence number of SNA requests/responses.  
  
- Any sense data (shown as "SENSE=...") on SNA responses or **Data** messages.  
  
- The acknowledgment required (ACKRQD) field in [Data](./data1.md) and [Status-Control](./status-control1.md) messages.  
  
- The relevant application flags in **Data** and **Status-Control** messages. (For more information, see [Application Flags](../core/application-flags1.md).)  
  
- The message key field in **Data** messages.  
  
- Any error codes (shown as "ERROR=...") in [Status-Acknowledge](./status-acknowledge1.md) or **Status-Control** messages.  
  
  For simplicity, it is assumed that all messages are function management data flowing on the same PLU session that:  
  
- Uses half-duplex flip-flop protocols.  
  
- Uses brackets, with reset state of between-bracket.  
  
- Does not use the PLU CICB segment delivery option. (For more information, see [Segment Delivery](../core/segment-delivery1.md)).  
  
## See Also  
 [Opening the PLU Connection](../core/opening-the-plu-connection1.md)   
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