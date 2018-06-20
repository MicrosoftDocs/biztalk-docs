---
title: "SSCP Session Characteristics2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6f82c167-3e3f-471f-a995-0540e7d63bb4
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SSCP Session Characteristics
For SNA type 2.1 nodes, the system services control point (SSCP) session uses function management (FM) profile 0 and Transmission Service profile (TS profile) 1. This combination of profiles provides the following session characteristics:  
  
- The primary and secondary half-sessions both use immediate request mode.  
  
- The primary and secondary half-sessions both use immediate response mode.  
  
- Only definite-response single request unit chains are allowed.  
  
- The maximum request unit size is limited to 256 bytes.  
  
- Data flow control request units are not supported.  
  
- Pacing is not supported.  
  
- Identifiers are used (rather than sequence numbers) on the normal flows.  
  
  This implies that the SSCP connection has the following characteristics:  
  
- All [Data](./data1.md) messages have the acknowledgment required (ACKRQD) field set.  
  
- All Data messages have the begin chain indicator (BCI) and end chain indicator (ECI) application flags set.  
  
- [Status-Control](./status-control1.md) messages do not flow on the connection.  
  
- [Status-Session](./status-session2.md) messages from the local node to the application only report changes in the activation state of the session.  
  
- The chaining, bracket, confirmation, and recovery protocols (described in [PLU Connection](../core/plu-connection2.md)) do not apply.  
  
  Using the SSCP connection, the application can send and receive **Data** messages corresponding to function management data network services (FMD NS) (session services) requests and FMD data requests. Examples of FMD NS (session services) requests are:  
  
- **INIT-SELF.** Requests from the secondary to the host SSCP requesting that the SSCP assist in the initiation of a session to the host PLU, effectively requesting a **BIND**. (For more information, see [Opening the PLU Connection](../core/opening-the-plu-connection1.md).)  
  
- **TERM-SELF.** Requests from the secondary to the host SSCP requesting that the PLU-SLU session be terminated with an **UNBIND**. (For more information, see [Closing the PLU Connection](../core/closing-the-plu-connection1.md).)  
  
- **Character-coded requests.** Requests such as logon, logoff, or test commands from the secondary display, or a logon prompt from the host application.  
  
- **NOTIFY.** Requests used by the secondary to notify the host SSCP that a device is available after a **BIND** was rejected with sense code 0x0845, for example, where a device emulator supports logical power-off.  
  
  The local node sends a **NOTIFY** request to the SSCP on behalf of the LU whenever the application's SSCP connection state changes while the LU is active. A **NOTIFY** (vector key 0x0C with byte 5 set to 0x03), which can act as secondary LU, is sent in the following cases:  
  
- When an [Open(SSCP) Request](./open-sscp-request2.md) is received when the LU is already active.  
  
- When an ACTLU request is accepted when the SSCP connection is already opened.  
  
  A **NOTIFY** (vector key 0x0C with byte 5 set to 0x01), which cannot currently act as secondary LU, is sent in the following cases:  
  
- When an ACTLU is received when the SSCP connection is not open.  
  
- When a [Close(SSCP) Request](./close-sscp-request2.md) is received when the PLU session is not bound.  
  
- When an **UNBIND** request is received when the SSCP connection is not open.  
  
- When the long response including the **NOTIFY** vector is used for ACTLU requests.  
  
  These **NOTIFY** messages can be used by the host in conjunction with the negative response 0x0845 that the local node gives to a **BIND** received when the SSCP connection is not open. (For more information, see [Opening the PLU Connection](../core/opening-the-plu-connection1.md).)