---
title: "Application Flags1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 364d7c17-320e-4786-92f7-bbe346d482ed
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Application Flags
Application flags are included on the following messages:  
  
- All [Data](./data1.md) messages (both inbound and outbound)  
  
- [Status-Acknowledge(Ack)](./status-acknowledge-ack-2.md) (outbound only)  
  
- [Status-Acknowledge(Nack-1)](./status-acknowledge-nack-1-1.md) (outbound only)  
  
- All [Status-Control](./status-control1.md) messages (both inbound and outbound)  
  
  These flags represent key indicators of the state of the session to which the message relates and are closely related (but not always equivalent) to the request header or response header (RH) indicators in the SNA request or response. Note that for inbound messages, applications need to set the flags on **Data** messages and **Status-Control** messages only.  
  
  For outbound messages, the local node sets the application flags to reflect the contents of the RH in the corresponding SNA message. The local node performs checks on the SNA message before sending it to the application. Therefore, the application can assume that the RH indicators follow the SNA protocols and need not perform its own checks. The application's task in interpreting the application flags is much simpler than if the local node presented the message with the uninterpreted RH. For example:  
  
- If the application specified the segment delivery option when the primary logical unit (PLU) connection was opened, the end chain indicator (ECI) on an SNA request will occur on the first segment of the last request/response unit (RU) in a chain, but the chain is not complete until the last segment of that RU is received. In this case, the local node manipulates the application flags so that the ECI flag is set in the last segment rather than the first. (For more information, see [Opening the PLU Connection](../core/opening-the-plu-connection1.md).)  
  
- Applications using Transmission Service profile 4 (TS profile 4) on the PLU session can receive the definite response 2 (DR2) RH indicator in combination with definite response 1 (DR1) or exception response (ER) to give RQD2, RQD3, RQE2, and RQE3 requests. The local node interprets the RH indicators and sets the **COMMIT** application flag accordingly.  
  
  For inbound [Data](./data1.md) and [Status-Control](./status-control1.md) messages, you should set the application flags to control session characteristics such as chaining, direction control, and brackets. For **Status-Acknowledge** messages, the local node generates an SNA response and sets the RH indicators using information saved from the corresponding request. The application does not need to set the flags on this message.  
  
  For information about application flag usage when you are using function management interface (FMI) chunking, see [Chunking](../core/chunking2.md).  
  
  In most cases, the application does not need to use the application flags on [Status-Acknowledge(Ack)](./status-acknowledge-ack-2.md) messages, which derive from the response header indicators on the corresponding response. However, certain applications do require access to the response header flags on responses. For example, transaction-processing applications using TS profile 4 can receive the DR2 flag on responses, which appear as the **COMMIT** flag in the application flags.  
  
  Application flag usage on [Status-Control](./status-control1.md) (SC) messages is derived from the response header indicators in the corresponding data flow control or session control request unit. Applications may need to be aware of the response header flags for Status-Control messages. For example, LUSTAT request type 6 is a no-op used solely to enable response header flags to be sent when no other request is allowed. The local node delivers the request to the application as a Status-Control(LUSTAT) Request with the relevant application flags set. For summaries of valid request header usage for data flow control request units and of valid response header indicators for SC requests, see *SNA Format and Protocol Reference Manual: Architectural Logic* (IBM publication SC30-3112).  
  
  In the summary of the application flags in the table that follows, bits are numbered with bit 0 as the most significant bit in a byte and bit 7 as the least significant. An application flag is set if the relevant bit for the flag is 1 and not set if the bit is 0.  
  
  Flag 1 occurs in all messages.  
  
  The following table lists the meanings of the individual bits.  
  
|Bits in flag 1|Meaning|  
|--------------------|-------------|  
|FMHI [bit 0, flag 1] Value: AF_FMH (0x80)|Function management header indicator. Set if a function management header is present in the message, or if the message is a function management data network services (FMD NS) request. Only valid on [Data](./data1.md) messages. This flag is always set for 3270 user alerts, which are sent on the system services control point (SSCP) connection. For more information, see [3270 User Alerts](../core/3270-user-alerts2.md).|  
|BCI [bit 1, flag 1] Value: AF_BC (0x40)|Begin chain indicator. Set if this message starts a chain. For more information, see [Outbound Chaining](../core/outbound-chaining2.md) and [Inbound Chaining](../core/inbound-chaining1.md).|  
|ECI [bit 2, flag 1] Value: AF_EC (0x20)|End chain indicator. Set if this message ends a chain. For more information, see **Outbound Chaining** and [Inbound Chaining](../core/inbound-chaining1.md).|  
|COMMIT [bit 3, flag 1] Value: AF_COMM (0x10)|Commit indicator. Set if chain carries DR2.|  
|BBI [bit 4, flag 1] Value: AF_BB (0x08)|Begin bracket indicator. Set if chain carries begin bracket (BB). Note that this does not necessarily indicate that the bracket has been initiated. For more information, see [Brackets](../core/brackets1.md).|  
|EBI [bit 5, flag 1] Value: AF_EB (0x04)|End bracket indicator—set if chain carries end bracket (EB). Note that this does not indicate that the bracket has terminated. For more information, see **Brackets** .|  
|CDI [bit 6, flag 1] Value: AF_CD (0x02)|Change direction indicator. Set if chain carries change direction (CD). For more information, see [Direction](../core/direction1.md).|  
|SDI [bit 7, flag 1] Value: AF_SD (0x01)|System detected error indicator. Set if the local node detects an error in outbound data. For more information, see [Outbound Data](../core/outbound-data1.md).|  
  
 Flag 2 occurs in all messages except **Status-Control(STSN)**, where the indicators included in this byte are not applicable.  
  
 The meanings of the individual bits are listed in the following table.  
  
|Bits in flag 2|Meaning|  
|--------------------|-------------|  
|CODE [bit 0, flag 2] Value: AF_CODE (0x80)|Alternate code indicator. Set if the alternate code set (usually ASCII) is used for this [Data](./data1.md) message. Note that function management headers are unaffected by the code selection indicator.|  
|ENCRYP [bit 1, flag 2] Value: AF_ENCR (0x40)|Enciphered data indicator. Set to indicate that the information in the **Data** message is enciphered under session level cryptography protocols. You must provide the necessary support for data encryption. The Host Integration Server local node does not support cryptography.|  
|ENPAD [bit 2, flag 2] Value: AF_ENPD (0x20)|Padded data indicator. Set in conjunction with the **ENCRYP** flag to indicate that the data was padded at the end to the next integral multiple of eight bytes before enciphering.|  
|QRI [bit 3, flag 2] Value: AF_QRI (0x10)|Queued response indicator. Set if the response to this request is to be queued in the transmission control and data flow control layers. This flag is only significant for inbound messages.|  
|CEI [bit 4, flag 2] Value: AF_CEI (0x08)|Chain ending indicator. Set on a message corresponding to an outbound SNA request with EC and begin basic information unit (BBIU). This flag is provided solely for the use of SNA server components. Your application should not attempt to use it.|  
|BBIUI [bit 5, flag 2] Value: AF_BBIU (0x04)|Begin basic information unit indicator. Set on a message corresponding to an outbound SNA request with BBIU. This flag is provided for the use of SNA server components and for applications using segment delivery and outbound pacing together. Your application should not attempt to use it. (For more information, see [Pacing and Chunking](../core/pacing-and-chunking1.md).)|  
|EBIUI [bit 6, flag 2] Value: AF_EBIU (0x02)|End basic information unit indicator. Set on a message corresponding to an outbound SNA request with end basic information unit (EBIU). This flag is provided solely for the use of SNA server components. Your application should not attempt to use it.|  
|RBI [bit 7, flag 2] Value: AF_RBI (0x01)|Real BID indicator. Set on **Status-Control(BID) Request** messages from the local node only. 0x01 indicates that the message is due to an SNA BID RU. 0x00 indicates that the message is due to an outbound function management data (FMD) RU with BB set.|  
  
## See Also  
 [Sessions and Connections](../core/sessions-and-connections2.md)