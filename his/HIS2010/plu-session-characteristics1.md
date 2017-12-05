---
title: "PLU Session Characteristics1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 64116056-6a21-4053-b6b1-e9ec9bf69c69
caps.latest.revision: 3
---
# PLU Session Characteristics
The local node provides support on the primary logical unit (PLU) session for function management (FM) profiles 2, 3, 4, and 7 and Transmission Service profiles (TS profiles) 2, 3, 4, and 7. Support of these profiles means that the local node supports LU-LU session types 0, 1, 2, and 3. Using the PLU connection, the application can send and receive any FM data that is valid for these LU-LU types.  
  
 The protocols appropriate to a particular session are determined by the parameters in the **BIND** request that establishes the session. The **BIND** parameters are reported to the application in the bind information control block (BICB) on the [Open(PLU) OK Confirm](../HIS2010/open-plu-oconfirm2.md) message. It is the application's responsibility to conform to the session protocols reported in the BICB.  
  
 Due to the wide range of **BIND** parameters allowable on a session and the options available to an application in the CICB on the [Open(PLU) OK Response](../HIS2010/open-plu-oresponse1.md), this section does not attempt a complete description of the protocols for a particular session. The remaining topics in this section describe the general protocol characteristics of the PLU session, such as chaining, brackets, and so on.  
  
 Most of the protocol descriptions in the remainder of this section are accompanied by figures to illustrate the important features. The figures show:  
  
-   The relevant response header flags in SNA requests/responses.  
  
-   The sequence number of SNA requests/responses.  
  
-   Any sense data (shown as "SENSE=...") on SNA responses or **Data** messages.  
  
-   The acknowledgment required (ACKRQD) field in [Data](../HIS2010/data2.md) and [Status-Control](../HIS2010/status-control2.md) messages.  
  
-   The relevant application flags in **Data** and **Status-Control** messages. (For more information, see [Application Flags](../HIS2010/application-flags2.md).)  
  
-   The message key field in **Data** messages.  
  
-   Any error codes (shown as "ERROR=...") in [Status-Acknowledge](../HIS2010/status-acknowledge2.md) or **Status-Control** messages.  
  
 For simplicity, it is assumed that all messages are function management data flowing on the same PLU session that:  
  
-   Uses half-duplex flip-flop protocols.  
  
-   Uses brackets, with reset state of between-bracket.  
  
-   Does not use the PLU CICB segment delivery option. (For more information, see [Segment Delivery](../HIS2010/segment-delivery2.md)).  
  
## See Also  
 [Opening the PLU Connection](../HIS2010/opening-the-plu-connection2.md)   
 [Outbound Chaining](../HIS2010/outbound-chaining1.md)   
 [Inbound Chaining](../HIS2010/inbound-chaining2.md)   
 [Segment Delivery](../HIS2010/segment-delivery2.md)   
 [Brackets](../HIS2010/brackets2.md)   
 [Direction](../HIS2010/direction2.md)   
 [Pacing and Chunking](../HIS2010/pacing-and-chunking2.md)   
 [Confirmation and Rejection of Data\]](../HIS2010/confirmation-and-rejection-of-data]2.md)   
 [Shutdown and Quiesce](../HIS2010/shutdown-and-quiesce2.md)   
 [Recovery](../HIS2010/recovery2.md)   
 [Application-Initiated Termination](../HIS2010/application-initiated-termination2.md)   
 [LUSTATs\]](../HIS2010/lustats]2.md)   
 [Response Time Monitor Data](../HIS2010/response-time-monitor-data2.md)