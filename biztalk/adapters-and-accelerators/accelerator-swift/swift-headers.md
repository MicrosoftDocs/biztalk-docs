---
title: "SWIFT Headers | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SWIFT, headers"
  - "headers [SWIFT]"
ms.assetid: b599cca2-8ae6-42db-b3a2-712ba12c1017
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SWIFT Headers
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provides the SWIFT header and trailer schemas. A4SWIFT has already incorporated these into the interchange schemas for the various financial (FIN) messages. If you want to create a custom SWIFT FIN format style message type (for example, an N98 message), you can incorporate the header and trailer schemas into your own format.  
  
 The SWIFT header schema (SWIFT Header.xsd) contains the formats for the following:  
  
- Basic Header  
  
- Application Header (choice of Input or Output)  
  
- User Header  
  
- Beginning delimiter of the text block  
  
  The Basic Header contains information about the source of the message. The Application Header contains information about the message type and the destination of the message. The resolution of the message type by the SWIFT disassembler in a receive pipeline is based on the contents of the field in the appropriate Application Header. The User Header is optional, and contains special processing instructions.  
  
> [!NOTE]
>  A few message types have variable formats based on the contents of field 119 in the User Header. These are "dual message types" in A4SWIFT. The A4SWIFT disassembler uses the message type in the Application Header in conjunction with the contents of field 119 to select the appropriate schema for a message instance.  
  
 The User Header is optional, and appears mainly for FIN-Copy use. The Service identifier in Block 1 must be "01". If the header is present, at least one of the fields must be present. However, all of the fields are optional. The fields in the User Header follow the same rules as those in the message text area.  
  
 The following table lists all of the SWIFT header field types.  
  
|Field type|Description|  
|----------------|-----------------|  
|**Application Identifier (Block 1)**|Designates the application that has established the association used to convey the message. You always use **F** for FIN messages.|  
|**Block Identifier (All)**|The first character inside the left curly brace. The Block Identifier is always followed by a colon.<br /><br /> **1** = Basic Header<br /><br /> **2** = Application Header<br /><br /> **3** = User Header<br /><br /> **4** = Message Text<br /><br /> (See values below for Trailer.)|  
|**Delivery Monitoring (Block 2) (optional)**|If the priority is **U**, delivery monitoring must be:<br /><br /> **1** = Non-Delivery Warning<br /><br /> Or<br /><br /> **3** = Non-Delivery Warning and Delivery Notification.<br /><br /> If the priority is **N**, delivery monitoring must be:<br /><br /> **2** = Delivery Notification<br /><br /> Or<br /><br /> Not included|  
|**Destination Address (Block 2)**|The full Logical Terminal (LT) address of the destination of the message being sent to the SWIFT network.|  
|**End Delimiter (Blocks All)**|You use the right curly brace (**}**) for the End Delimiter.|  
|**Input/Output Identifier (Block 2)**|**I** = messages sent to SWIFT.<br /><br /> **O** = messages sent from SWIFT.|  
|**Input Time and Date (Block 2)**|The hour (HH) and minute (MM) followed by the year (YY), month (MM) and Day (DD) on which the sender sent the message to SWIFT. The Input Time and Date is always local to the sender of the message.|  
|**Logical Terminal (LT) Address (Block 1)**|The logical terminal address of the sender for messages sent or the receiver for messages received from the SWIFT network.|  
|**Message Input Reference (MIR) (Block 2)**|The date the sender sent the message to SWIFT written in the format, year (YY), month (MM), and Day (DD). The MIR is always local to the sender of the message, and is followed by the full LT address of the sender of the message, and the sender's session and sequence to SWIFT.|  
|**Message Priority (Block 2)**|Priority of the message; "S" for system messages (types 000—099); "U" for Urgent or "N" for user-to-user messages (types 100—999).|  
|**Message Type  (Block 2)**|Three-digit FIN message type, 000 – 999.|  
|**Obsolescence Period  (Block 2--optional)**|Default value of 3 units (15 minutes) for Priority U and 20 units (100 minutes) for Priority N. (Default values always used. Valid only if Delivery Monitoring is present.|  
|**Output Date (Block 2)**|The output date, local to the receiver, written in the following format: YYMMDD.|  
|**Output Time (Block 2)**|The output time, local to the receiver, written in the following format: HHMM.|  
|**Sequence Number (Block 1)**|For all FIN messages with a Service Identifier of **01** or **05**, this number is the next expected sequence number appropriate to the direction of the transmission.<br /><br /> For FIN messages with a Service Identifier of **21** or **25**, the sequence number is that of the acknowledged service message.|  
|**Service Identifier (Block 1)**|A two-digit number identifying the type of service message, appropriate to the FIN application. For all messages of types 000 to 999 for FIN, use **01**. For all messages of types 02 to 43, use their two-digit service message type.|  
|**Session Identifier (Block 1)**|As appropriate, the current application session number based on the Login.|  
|**Start Delimiter (All Blocks)**|The left curly brace: **{**.|  
  
## See Also  
 [Working with Schemas](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)