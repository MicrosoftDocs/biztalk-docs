---
title: "Inbound Chaining1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e508dcfa-829d-4712-a9e6-137f7c4c1897
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Inbound Chaining
The division of application data into [Data](./data1.md) messages and the control of inbound chaining are the responsibility of the application.  
  
 The secondary maximum send request unit size for the session is a parameter in the **BIND** from the host and is available in the bind information control block (BICB) on the [Open(PLU) OK Confirm](./open-plu-oconfirm1.md) message. The application should ensure that each inbound **Data** message corresponds to a single request unit. It does not contain more data than the maximum request unit size given in the BICB.  
  
 The application should use the begin chain indicator (BCI) and end chain indicator (ECI) application flags in the **Data** message headers to control chaining. (For more information, see [Application Flags](../core/application-flags1.md).) The chain is the unit of recovery, and if recoverable errors occur in the chain, the application should assume responsibility for recovery. (For more information, see [Recovery](../core/recovery1.md).)  
  
 An inbound chain can terminate in the following ways:  
  
- The complete chain is sent without errors. All the **Data** messages in the chain have been passed to the host. If the session allows the secondary to send definite-response chains, and the application sets the **ACKRQD** field in the last **Data** message of the chain, the application receives a [Status-Acknowledge(Ack)](./status-acknowledge-ack-2.md) from the local node when the host supplies a response.  
  
- The local node detects a critical error in the format of a **Data** message from the application or in the state of the session. The local node rejects the **Data** message with a [Status-Acknowledge(Nack-2)](./status-acknowledge-nack-2-2.md) containing an error code and closes the PLU connection. Note that the local node will generate an inbound **CANCEL** request before closing the PLU connection. The local node will send a **TERM-SELF** request to the host to elicit an **UNBIND**.  
  
- The host sends a negative response to a request in the chain. The local node sends a [Status-Acknowledge(Nack-1)](./status-acknowledge-nack-1-1.md) message to the application with the sense codes and sequence number from the negative response. If the host rejects a request that does not carry the ECI application flag, and the application does not specify the application cancel option in the PLU CICB, the local node also generates an inbound CANCEL request. When the application specifies application cancel, it must send EC or **Status-Control(CANCEL)** to terminate the chain. Any subsequent inbound chains are rejected with a noncritical **Status-Acknowledge(Nack-2)**, sense code 0x2002 or 0x2004 (chaining or direction). When the application receives the **Status-Acknowledge(Nack-1)** message, it should stop sending data after this chain for half-duplex flip-flop sessions because the direction has passed to the host. (For more information, see [Direction](../core/direction1.md).)  
  
- The application cancels the chain while sending, by sending a **Status-Control(CANCEL)** message to the local node. The local node sends a CANCEL request to the host and sends a **Status-Control(CANCEL)** Acknowledge to the application on receiving a positive response from the host. Responses from the host to requests sent before the **CANCEL** will generate appropriate **Status-Acknowledge** messages to the application if the original [Data](./data1.md) messages had the **ACKRQD** field set.  
  
- The application closes the PLU connection while sending the chain. The local node sends a **Close(PLU) Response** to the application. Responses from the host to requests sent before the **Close(PLU)** message will not generate **Status-Acknowledge** messages to the application. Note that the local node will also generate an inbound **CANCEL** request and a **TERM-SELF** request to elicit an **UNBIND**.  
  
  If the local node detects a noncritical error in the format of a **Data** message from the application or the state of the session, it does not close the PLU connection. Instead, it rejects the **Data** message in error with a **Status-Acknowledge(Nack-2)** containing an appropriate error code. No data is sent to the host.  
  
  If an inbound chain terminates with an error, when the session uses half-duplex protocols, the application must assume a receive state. (For more information, see [Recovery](../core/recovery1.md).)  
  
  The following six figures illustrate inbound chaining protocols between the local node and the application, and how those protocols relate to the underlying SNA protocols.  
  
  In the first figure, a complete inbound chain is sent without error and accepted by the host. Note that after receiving **Status-Acknowledge(Ack)** the application relinquishes direction to the host.  
  
  ![](../core/media/his-32703j.gif "his_32703j")  
  Inbound chain is sent without error and accepted by the host  
  
  In the following figure, the local node detects a critical error in the format of the second **Data** message in the chain (**ACKRQD** without the ECI application flag), sends a **Status-Acknowledge(Nack-2)** to the application with the appropriate error code, and closes the PLU connection. Note that the local node only generates the **CANCEL** if the session's function management (FM) profile supports **CANCEL**.  
  
  ![](../core/media/his-32703ja.gif "his_32703ja")  
  Local node detects error, sends a Status message, and closes the PLU connection  
  
  In the following figure, a complete inbound chain is sent without error, but is rejected by the host. After the negative response, the application must enter receive state, pending error recovery. (For more information, see [Recovery](../core/recovery1.md).)  
  
  ![](../core/media/his-32703jb.gif "his_32703jb")  
  Inbound chain is sent without error but is rejected by host  
  
  In the following figure, the application cancels the chain by sending **Status-Control(CANCEL)**. Note that the application still has direction and can start a new chain.  
  
  ![](../core/media/his-32703jc.gif "his_32703jc")  
  Application cancels the chain with a Status-Control(CANCEL)  
  
  In the following figure, the application closes the PLU session while sending the chain. The local node only generates the **CANCEL** if the session's FM profile supports **CANCEL**.  
  
  ![](../core/media/his-32703jd.gif "his_32703jd")  
  Application closes the PLU connection while sending the chain  
  
  In the following figure, the local node detects a noncritical error in the format of the second **Data** message in the chain and sends a **Status-Acknowledge(Nack-2)** to the application with the appropriate error code.  
  
  ![](../core/media/his-32703je.gif "his_32703je")  
  Local node detects a noncritical error and sends a Status-Acknowledge(Nack-2)  
  
## See Also  
 [Opening the PLU Connection](../core/opening-the-plu-connection1.md)   
 [PLU Session](../core/plu-session2.md)   
 [Outbound Chaining](../core/outbound-chaining2.md)   
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