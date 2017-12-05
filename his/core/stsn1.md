---
title: "STSN1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5492645a-213e-47ad-aa0e-26c1a6616095
caps.latest.revision: 3
---
# STSN
Set and test sequence numbers (STSN) are used on sessions with Transmission Service profile (TS profile) 4 for applications to maintain transaction processing sequence numbers between sessions. This enables both partners on the session to discover the amount of data lost after a **CLEAR** or **UNBIND–BIND** sequence.  
  
 The **STSN** message is the only one that can reset such transaction processing sequence numbers. **BIND**, **UNBIND**, and **CLEAR** do not affect them.  
  
 If the application wants to maintain such transaction numbers, it must specify the **APPLTRAN** option in the [Open(PLU) OK Response](../core/open-plu-oresponse1.md). The host can send **STSN** after a **BIND** or **CLEAR** before sending **SDT** to set or test the application's transaction numbers. The local node resets its internal session sequence numbers to zero on receipt of **BIND** or **CLEAR**. When the local node receives an **STSN** specifying **SET** (or **SET** and **TEST**) for one half-session, it resets the corresponding internal session sequence number.  
  
 Unless both half-session actions are ignore (the action byte is 0x00), the **STSN** request is passed to the application (provided that it specified **APPLTRAN**), with the action byte and the two sequence numbers from the request, as a **Status-Control(STSN)**. (For more information, see [Status-Resource](../core/status-resource2.md).) The application must examine the action byte to determine whether the action is ignore, set, test, or set and test. The application must send a positive response (**Status-Control(STSN) Acknowledge**) to the **STSN**, with the sensed sequence numbers if required (sense or set and test). The local node is responsible for generating the correct result code for the **STSN RSP**.  
  
 Note that the application should perform the sense part of **STSN** first (by examining bits 0 and 2 of the action byte for the secondary-to-primary flow and primary-to-secondary flow respectively). The set part of the **STSN** is then performed (by examining bits 1 and 3 of the action byte).  
  
 The application should increment its transaction numbers when sending and receiving normal flow request/response units (RUs) from the host. (Note that **Status-Control** messages corresponding to normal flow data flow control (DFC) requests cause the transaction numbers to be incremented.) The sequence number is reported on **DATAFMI** messages and **Status-Acknowledge** messages. The application should be aware that, if a message from the host fails receive checks (and is converted to an **SDI** message), sub-network access protocol (SNAP)-2.1 will purge the remainder of the chain from the host, and the application may miss some sequence numbers. Therefore, the application should reset its primary-to-secondary transaction number from the next outbound data after processing an **SDI** message.  
  
 Note that the second application flag byte is not valid for **Status-Control(STSN)**. It is used for the **STSN** control byte.  
  
## See Also  
 [Application CANCEL](../core/application-cancel1.md)   
 [Direction after Receiving a Negative Response](../core/direction-after-receiving-a-negative-response2.md)   
 [Direction after Sending a Negative Response](../core/direction-after-sending-a-negative-response1.md)   
 [Critical Failure](../core/critical-failure1.md)   
 [RQR and CLEAR](../core/rqr-and-clear2.md)   
 [Link Service Failure](../core/link-service-failure2.md)   
 [Local Node Failure](../core/local-node-failure1.md)   
 [Client Failure](../core/client-failure2.md)