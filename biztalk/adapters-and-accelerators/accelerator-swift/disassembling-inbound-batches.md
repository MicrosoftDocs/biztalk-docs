---
title: "Disassemble Inbound Batches with SWIFT | Microsoft Docs"
description: Debatch inbound message, and customize schemas for batching using the SWIFT Accelerator in BizTalk Server
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 11cb5672-1155-4648-b1fd-c9a3bc30e351
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Disassemble Inbound Batches

## Debatch inbound message
The SWIFT disassembler is able to inbound debatching in which it processes or disassembles inbound batches (files or messages containing multiple SWIFT messages). You enable inbound debatching using the SWIFT disassembler configuration property of the same name. After you enable inbound debatching, the SWIFT disassembler expects all messages that it receives to be batches that include multiple SWIFT messages. A batch may or may not include a batch envelope (a batch header and a batch trailer), and each individual SWIFT message within a batch may or may not include a message envelope (a message header and a message trailer). You can configure these batch attributes (formats) using the following SWIFT disassembler configuration properties:  
  
- Batch Header Schema  
  
- Batch Trailer Schema  
  
- Message Header Schema  
  
- Message Trailer Schema  
  
  > [!NOTE]
  >  Setting any of these properties to "None" indicates that the inbound batch does not include that particular part.  
  
  The SWIFT disassembler expects all inbound batches to have the following structure:  
  
  **Batch Header**  
  
  **Message Header**  
  
  **SWIFT Interchange/Message (SWIFT Blocks 1 to 5)**  
  
  **Message Trailer**  
  
  **Batch Trailer**  
  
  Within this structure, you can consider a "message block" to be the **Message Header – SWIFT Interchange – Message Trailer** parts. A series of multiple "message blocks" makes up the multiple SWIFT messages in a batch. The Batch Header, Message Header, Message Trailer, and Batch Trailer are optional, but must be consistent across repetitions.  
  
> [!NOTE]
>  Do not confuse the message envelope (Message Header and Message Trailer) with the SWIFT header and trailer blocks. In the context of batches, you should view the SWIFT message (interchange), including the SWIFT header and trailer blocks, as a holistic (atomic) unit. In this context, the Message Header and Message Trailer refer to the envelope that wraps each SWIFT message in a batch.  
  
 To express this structure, its options, and its repeatability more formally, consider how [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] defines a batch:  
  
- **Batch Header** is represented by **BH**  
  
- **Message Header** is represented by **MH**  
  
- **SWIFT Interchange** is represented by **SI**  
  
- **Message Trailer** is represented by **MT**  
  
- **Batch Trailer** is represented by **BT**.  
  
  The expression that represents the expected batch structure is as follows:  
  
  `[BH] ([MH] SI [MT])* [BT]  `
  
  The brackets ( `[ ] ` ) indicate that the part is optional. The asterisk (**\\***)indicates that the block is repeatable. Whoever builds the message batch must use the message header (*<em>MH</em>*) and trailer (*<em>MT</em>*) consistently in each repetition of (`[MH] SI [MT]`).  
  
  The SWIFT disassembler is able to process any inbound batch that obeys the above structure, because each part in the structure conforms to a flat-file schema. However, if you do not use the optional batch header/trailer and message header/trailer, the message will not conform to those schemas. As a result, a batch containing only consecutive SWIFT messages will have the Batch Header Schema, Batch Trailer Schema, Message Header Schema, and Message Trailer Schema properties set to "None".  

## Customize schemas for batching  
 You can customize the schemas for the batch header/trailer and message header/trailer. An example is the following batch:  
  
```  
4  
SWIFT Message # 1  
$  
SWIFT Message # 2  
$  
SWIFT Message # 3  
$  
SWIFT Message # 4  
$  
```  
  
 To handle this type of batch, you would set the schema properties for the batch as follows:  
  
- You set the Batch Header Schema property to a flat-file schema that parses a single number (message count) delimited by carriage-return.  
  
- You set the Message Trailer Schema to a flat-file schema that parses a single $ symbol and carriage-return.  
  
- You set the remaining envelope schemas (Batch Trailer Schema and Message Header Schema) to None.  
  
  You can configure the SWIFT disassembler such that it processes just about any SWIFT message batch by creating and specifying the appropriate combination of flat-file envelope schemas. This functionality is very flexible.  
  
  The SWIFT disassembler always attempts to complete processing of an entire batch, even when it encounters errors along the way. This enables it to collect and report as many errors as possible all at once. To perform this "best effort" heuristic, the SWIFT disassembler must make certain decisions and assumptions when selecting the schema to use upon encountering a new part, or if a parsing error occurs. Selecting the correct schema is not always possible depending upon the nature and location of a parse error and the ambiguity/similarity between envelope schemas and the SWIFT interchange schemas. In some cases, you can minimize the possibility of selecting the wrong schema by using well-designed envelope schemas. If the disassembler encounters a fatal parse error or the disassembler cannot determine the correct schema, the disassembler will fail the batch without processing the remaining data.  
  
  When **Inbound Debatching** is **enabled** (set to **True**), the SWIFT disassembler parses the batch using the schemas specified for the batch envelope (Batch Header Schema and Batch Trailer Schema) and message envelope (Message Header Schema and Message Trailer Schema), as well as the schema specified for parsing the SWIFT messages (interchanges) in the batch. For the SWIFT messages in the batch, the message type and schema can be dynamically discovered and loaded in the same way as single non-batch messages (by specifying a SWIFT Header Schema). For more information about how the SWIFT disassembler performs schema resolution, see [Dynamic Message Type Discovery and Schema Resolution](../../adapters-and-accelerators/accelerator-swift/dynamic-message-type-discovery-and-schema-resolution.md).  
  
  The SWIFT disassembler parses and validates each SWIFT message in an inbound batch individually. It performs the following batch processing sequence:  
  
1. Parses the batch header if you have specified the Batch Header Schema.  
  
2. Parses the message envelope header if you have specified the Message Header Schema.  
  
3. Parses the SWIFT interchange (message).  
  
4. Validates the SWIFT message against XML constraints if you have enabled XML validation.  
  
5. Validates the SWIFT message against BRE policies (SWIFT network and usage rules) if you have enabled BRE validation.  
  
6. Parses the message envelope trailer if the Message Trailer Schema is specified.  
  
7. Repeats Steps 2 to 6 until the disassembler does not find any more messages in the batch.  
  
8. Parses the batch trailer if you have specified the Batch Trailer Schema.  
  
   You can configure the SWIFT disassembler to do different things with the batch data that it parses and validates using the following SWIFT disassembler configuration properties:  
  
- The **Fragmentation** property determines if the SWIFT disassembler should publish each message in the batch to the MessageBox database individually (that is, for each message, after each occurrence of Step 6 above), or if it should complete all of steps 1 to 8 and then publish the entire batch, in native form (exact copy of input), as a single message to the MessageBox database. You set **Fragmentation** to **True** to enable fragmentation and publish messages from a batch individually. You set **Fragmentation** to **False** to disable fragmentation and publish the entire batch, in native form, as a single message only after processing the entire batch. Typically, set **Fragmentation** to **Disabled**for scenarios when you only need the BizTalk Accelerator for SWIFT ([!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]) to parse and validate inbound batches and either failed, or forwarded, in the same form that [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] received them. You usually set **Fragmentation** to **Enabled** for scenarios in which you want [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to transform or modify messages within a batch after parsing and validation, or when you want [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to re-sort messages in a batch to an order different from what [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] originally received them in. You also set **Fragmentation** to **Enabled** for scenarios in which an inbound batch contains messages that have differing final destinations.  
  
- The **Preserve Batch Header / Preserve Batch Trailer** property determines if the SWIFT disassembler should discard or preserve the batch envelope (header and trailer) data after parsing it. If you set **Preserve Batch Header or Preserve Batch Trailer** to **True**, the disassembler publishes the corresponding batch part (parsed XML) to the MessageBox database as individual messages. The disassembler publishes the data in the body part of the multi-part message. The disassembler promotes special context properties so that [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] can correlate these messages to the batch that they came from and the ordinal position they were in within the batch (first position for batch header, last position for batch trailer). If you set **Preserve Batch Header or Preserve Batch Trailer** to **False**, the disassembler discards the corresponding batch part (parsed data) after parsing.  
  
  > [!NOTE]
  >  These configuration properties are valid only when fragmentation is enabled (**Fragmentation** set to **True**). When fragmentation is disabled, the disassembler publishes an exact copy of the entire batch, in native form, to the MessageBox database, so preservation settings are irrelevant (*everything* is preserved).  
  
- The **Preserve Message Header** / **Preserve Message Trailer** property determines if the SWIFT disassembler should discard or preserve the message envelopes (message headers and trailers) after parsing them. If you set **Preserve Message Header or Preserve Message Trailer** to **True**, the disassembler publishes the corresponding batch part (parsed XML) to the MessageBox database *along with the individual SWIFT message that it wraps*. The disassembler publishes message envelope headers in the **header** part of the multi-part message. The disassembler publishes message envelope trailers in the **trailer** part of the multi-part message. The disassembler publishes the SWIFT message contained in the message envelope in the **body** part of the same multi-part message. The disassembler promotes special context properties so that [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] can correlate these messages to the batch they came from and the ordinal position that they were in within the batch. If you set **Preserve Message Header or Preserve Message Trailer** to **False**, the disassembler discards the corresponding batch part (parsed data) after parsing.  
  
  > [!NOTE]
  >  These configuration properties are valid only when fragmentation is enabled (**Fragmentation** set to **True**). When fragmentation is disabled, the disassembler publishes an exact copy of the entire batch, in native form, to the MessageBox database, so preservation settings are irrelevant (*everything* is preserved).  
  
  For more information about each configuration property, as well as other usage and configuration information, see [SWIFT Disassembler Configuration Properties](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md). For more information about MessageBox database publishing and multi-part messages, see BizTalk Server Help.  
  
## Next step
  
[Batch-Related Promoted Properties](batch-related-promoted-properties.md)
