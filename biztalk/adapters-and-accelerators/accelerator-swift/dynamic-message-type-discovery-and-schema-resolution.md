---
title: "Dynamic Message Type Discovery and Schema Resolution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "dynamic schema resolution"
  - "disassembler, code sample"
  - "schemas, dynamic resolution"
  - "assembler, message types"
  - "disassembler, message types"
  - "code samples, disassembler"
ms.assetid: 5f71d3df-a37e-4ef2-9055-b614656203e9
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Dynamic Message Type Discovery and Schema Resolution
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] enables dynamic message type discovery and schema resolution in both the SWIFT disassembler and assembler.  
  
## SWIFT Disassembler  
 The SWIFT disassembler (DASM) has the ability to dynamically discover the message type of a received message and load the appropriate schema needed to parse the message. The greatest benefit of this feature is that you can configure a single pipeline using the SWIFT disassembler to process SWIFT messages of any SWIFT message type. Unlike the native BizTalk flat-file disassembler, the SWIFT disassembler does not require that you build a separate receive pipeline for each message type that A4SWIFT might encounter.  
  
 You can use dynamic message type discovery if you assume that, in most cases, all messages that a system receives will begin with structurally homogeneous header data. Within the header data are fields that reveal the message type of the message. For SWIFT messages, header data consists of SWIFT message blocks 1, 2, and 3, with message type information contained in block 2 (known as the Application Header).  
  
 The SWIFT DASM component can process all "single" (non-batched) SWIFT Messages out of the box without requiring any of the properties to be set. By default, the SWIFT Interchange Schema and SWIFT Header schema are not set; however, the SWIFT DASM component will use the SWIFT Header schema present in Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll to detect the SWIFT Message Type dynamically and process the messages. Also, BRE and XML Validation are enabled by default so any message that is processed will be completely validated. Setting the SWIFT Header schema property to point to the SWIFT Header in RuntimeSchemas.dll will also result in the same behavior as above.  
  
 When the SWIFT Header Schema configuration property for the SWIFT disassembler is set to "None" (the default), the disassembler dynamically resolves and loads the appropriate schema by performing the following steps:  
  
1. Uses the user-specified header schema (specified by the SWIFT Header Schema configuration property) to parse the beginning (header) of the receive message.  
  
2. Inspects the resulting "header XML" for the A4SWIFT_MessageType promoted property field. If this field exists, it uses the field value as the "message type" and proceeds to Step 4. If the field does not exist, it proceeds to Step 3.  
  
3. Inspects the header XML for the A4SWIFT_MessageType2 promoted property field (expected if the disassembler does not find the A4SWIFT_MessageType field). Uses the A4SWIFT_MessageType2 field value as the "message type".  
  
4. If the "message type" identified in Step 2 or 3 is "574", the SWIFT disassembler checks if the message type "574" is in the list of message types specified in the Dual Type Message List configuration property (which is a property of the disassembler). If yes, it proceeds to Step 5. If no, proceeds to Step 6.  
  
5. Inspects header XML for the A4SWIFT_SecondaryMessageType promoted property field. If this field exists, the disassembler uses the field value (for example, "IRSLST") as the "message sub-type" and appends it to the "message type", for example, "574_IRSLST".  
  
   > [!IMPORTANT]
   >  The explanation given for Step 5 is a simplification of what the SWIFT disassembler actually does to evaluate message sub-type. In actuality, the SWIFT disassembler uses the following algorithm to determine if a message type has sub-types, and if so, what that sub-type is as follows.  
  
   ```  
   Given MT type number nxx ...  
   if nxx is in the Dual-Type list {  
     if field 119 exists AND field 119 is NOT null/empty {  
       if n == 1 {  
         if field 119 == "STP" {  
           Use MTnxxPLUS schema  
         } else if field 119 == "REMIT" {  
           Use MTnxx schema  
         } else {  
           Use MTnxx_<field 119> schema  
         }   
       } else {  
         // n != 1  
         Use MTnxx_<field 119> schema  
       }  
     } else {  
       // field 119 does not exist or 119 does exist but is null/empty  
       Use MTnxx schema  
     }  
   } else {  
     // nxx is not a dual-type message  
     Use MTnxx schema  
   }  
   ```  
  
6. The disassembler now knows the message type, and it can form the interchange schema name by concatenating some fixed schema naming prefixes and suffixes (such as "MT" in the prefix to make "MT574_IRSLST").  
  
7. Loads the interchange schema (by name) and parses the entire message, **starting from the beginning**, using the loaded schema (this means that the disassembler parses the header data twice: once using the header schema, and again using the beginning of the interchange schema). The interchange schema must be able to parse the entire message, including the header.  
  
   > [!NOTE]
   >  The disassembler can use all A4SWIFT SWIFT message schemas to parse the entire SWIFT interchange (SWIFT blocks 1, 2, 3, 4, and 5). The disassembler uses the default SWIFT header schema to parse blocks 1, 2, and 3 only. See below for details.  
  
   The schema resolution algorithm described above implies that in order for dynamic message type discovery to work, the SWIFT Header Schema must contain fields that the disassembler has promoted using the following promoted properties (defined in the A4SWIFT Property Schema, Microsoft.Solutions.A4SWIFT.Property.PropertySchema):  
  
- **A4SWIFT_MessageType**  
  
- **A4SWIFT_MessageType2** (optional if **A4SWIFT_MessageTypes** is used)  
  
- **A4SWIFT_SecondaryMessageType** (optional)  
  
  For more information about these and other promoted properties, see [A4SWIFT_* Promoted Properties](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md).  
  
> [!NOTE]
>  If you set the SWIFT Header Schema to **None**, you should specify a complete interchange schema for the **SWIFT Interchange Schema** property. In this case, the disassembler uses the specified interchange schema to parse all messages that A4SWIFT receives. That is, you disable dynamic schema resolution and configure the pipeline to receive only messages whose type matches the specified interchange schema.  
  
 A4SWIFT installs a default SWIFT header schema (Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema) that can parse SWIFT standard header data and has the necessary promoted properties to facilitate dynamic schema resolution.  
  
 The default SWIFT header schema has the following promoted fields:  
  
- **SWIFTHeader/ApplicationHeaderBlock_Input/MessageType**. The disassembler promotes this using the **A4SWIFT_MessageType** property.  
  
- **SWIFTHeader/ApplicationHeaderBlock_Output/MessageType**. The disassembler promotes this using the **A4SWIFT_MessageType2** property.  
  
- **SWIFTHeader/UserHeaderBlock/ValidationFlag_119**. The disassembler promotes this using the **A4SWIFT_MessageType** property.  
  
  The disassembler uses **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema** by default as the header schema if you set both SWIFT Header Schema and SWIFT Interchange Schema configuration properties to "None".  
  
## SWIFT Assembler  
 Like the SWIFT disassembler, the SWIFT assembler has the ability to dynamically discover the message type of an outbound message and load the appropriate schema needed to serialize the message. This feature enables you to configure a single pipeline using the SWIFT assembler to process SWIFT messages of any SWIFT message type. Unlike the native BizTalk flat-file assembler, the SWIFT assembler does not require you to build a separate send pipeline for each message type that A4SWIFT might encounter.  
  
 Dynamic schema resolution in the SWIFT assembler is much simpler than in the SWIFT disassembler because the assembler does the job of serializing XML back into SWIFT flat-file format. The XML that [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] gives to the SWIFT assembler for serialization contains the message type and schema information, which the SWIFT assembler can use directly to load the appropriate schema for serialization. As such, the SWIFT assembler does not have any configurability for header and interchange schemas: it always uses the schema specified in the XML that it will serialize.  
  
## See Also  
 [Working with the SWIFT Disassembler and Assembler](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)