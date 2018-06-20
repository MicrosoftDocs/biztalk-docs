---
title: "MLLP Receive Adapter Processing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MLLP-encoded messages, receive adapters"
  - "MLLP adapters, send adapters"
  - "receive adapters"
ms.assetid: 03c9a5f6-6f23-454f-8bab-e7c7b6057efa
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MLLP Receive Adapter Processing
The Minimal Lower Layer Protocol (MLLP) receive adapter supports both one-way and two-way request response modes. The adapter listens and accepts connections.  
  
 When the MLLP receive adapter operates in two-way mode, the adapter will not receive a new message from the connection until the pipeline has generated the acknowledgment (ACK) for the previous message.  
  
## Configuration Parameters  
 The parameters for a receive handler are configured at the BizTalk Host level, and apply to all MLLP receive locations associated with it.  
  
|Parameter|Use|  
|---------------|---------|  
|*Max Accept Connection Limit*|Limits the number of concurrent open connections that the receive adapter will accept.|  
  
## Acknowledgments with the two-way MLLP receive adapter  
 When a two-way MLLP receive adapter receives a message, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) can generate the following types of ACKs:  
  
- HL7 Enhanced Commit ACK: In this scenario, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends a Commit ACK on the same connection. It sends out an Application Accept ACK on a different send port.  
  
- Application Accept ACK: In this scenario, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends an Application Accept ACK on the same connection.  
  
- Static ACK: In this scenario, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends an ACK on the same connection.  
  
- The type of ACK generated depends on the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer settings for the party sending the message. The value in fields MSH 15 and 16 of an individual message can override this setting. However, for applications expecting Static ACKs, the configuration can only be set through [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.  
  
## Error Conditions  
 The following events occur when there is an error condition or inactivity:  
  
- If the receive location is disabled or [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] shuts down, the following occurs:  
  
  - The receive location will no longer accept new connections.  
  
  - For existing connections, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] completely receives the current message, and then closes the connection.  
  
- When inactivity is detected (no payload data received on the receive location within the specified timeout), the adapter closes the connection.  
  
- If [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] receives an incomplete message, the portion received is suspended. All bytes received outside of a message (before the first SB on a new connection, between EB/CR and SB of the next message) are ignored.  
  
- If the pipeline fails to parse the message, the message is still delivered to the MessageBox database, with a promoted property **ParseError=true**.  
  
- If a message fails due to the absence of a subscription, or due to structural errors in the header, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] suspends the message in its original "wire" form (prior to being parsed). A frequent reason for the no-subscription failure is the lack of promoted properties. Since [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] suspends the unparsed message, the **BTS.MessageType** will be blank.  
  
  The following table lists the errors that the MLLP receive adapter returns.  
  
|            Event             |  ID  |                                                                                                          Error Condition                                                                                                           |
|------------------------------|------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **ErrorListening**      | 8448 |                                                   Could not bind to a local socket (most likely some other local application is using the same IP address/port ID combination).                                                    |
| **ErrorAcceptingConnection** | 8449 | Could not establish a TCP connection with the remote party. Either [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] reached the maximum connection limit, or the resources were insufficient. |
|  **ErrorSubmittingMessage**  | 8452 |                   The MessageBox database could not accept the message. Either [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] was unavailable or the resources were insufficient.                   |
|     **ErrorSendingAck**      | 8454 |                                [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] could not return the acknowledgment because the connection was not available.                                 |
  
## Performance Counters  
 The following table lists the performance counters that the MLLP adapter uses.  
  
|Counter|Meaning|  
|-------------|-------------|  
|Bytes|Size of the payload of all documents received or sent.|  
|Bytes/sec|Current throughput of the payload received or sent.|  
|Documents processed|**MLLP Receive**:<br /><br /> Number of documents successfully delivered to the MessageBox database.<br /><br /> **MLLP Send**:<br /><br /> Number of documents successfully delivered to the remote application.|  
|Documents failed|**MLLP Receive**:<br /><br /> Number of documents not successfully delivered to the MessageBox database.<br /><br /> **MLLP Send**:<br /><br /> Number of documents not successfully delivered to the remote application.|  
|Connection status|The status of the adapter connection, 1 or 0 (1=connected).|  
  
 The performance counter instances use the following naming scheme:  
  
```  
{recv|trans} : connection name : remote IP address : remote port ID  
```  
  
 Where the MLLP receive adapter uses the "recv" prefix, and the MLLP send adapter uses "trans".  
  
> [!NOTE]
>  ACKs sent by receive ports (for example, an adapter operating in a two-way mode) and send ports (operating to receive ACKs on the same socket connection) are not counted.  
  
## See Also  
 [Processing MLLP-encoded Messages](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)   
 [Configuration Parameters for Send and Receive Adapters](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md)   
 [MLLP Send Adapter Processing](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md)   
 [Setting Up a Send Port for Receiving ACKs](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)