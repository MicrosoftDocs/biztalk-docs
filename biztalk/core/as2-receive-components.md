---
title: "AS2 Receive Components | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bdab87fd-15b9-4e3c-a4d7-984693262293
caps.latest.revision: 26
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# AS2 Receive Components
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses several components to receive AS2 messages.  
  
## AS2 Receive Pipelines  
 Most AS2 receive processing is performed in the following AS2 receive pipelines. These pipelines are installed in `Microsoft.BizTalk.EdiInt.PipelineComponents.dll` in \Program Files\Microsoft BizTalk Server 20xx\Pipeline Components\\.  
  
 **AS2EdiReceive Pipeline**  
  
 This pipeline processes EDI messages received over AS2, including MDNs. The pipeline consists of the following pipeline components:  
  
- AS2 Decoder  
  
- EDI Disassembler  
  
- BatchMarker.  
  
  > [!NOTE]
  >  When using the AS2EdiReceive pipeline, you must add the user account that the BizTalk Isolated Host Instance process is running under to the BizTalk Application Users group. The AS2EdiReceive pipeline executes in the BizTalk Isolated Host Instance process. The AS2EdiReceive pipeline accesses the SSO store, which requires that the user is in the BizTalk Application Users group.  
  
  **AS2Receive Pipeline**  
  
  This pipeline processes messages received over AS2 when the messages are not encoded in EDI. These messages are treated as binary messages. The pipeline also processes MDNs received over AS2. The pipeline consists of the following pipeline components:  
  
- AS2 Decoder  
  
- AS2 Disassembler.  
  
## AS2 Receive Pipeline Components  
 The AS2 receive pipelines use the following pipeline components. These components are installed in `Microsoft.BizTalk.EdiInt.PipelineComponents.dll` in \Program Files\Microsoft BizTalk Server 20xx\Pipeline Components\\.  
  
> [!NOTE]
>  The AS2 Receive pipeline is only supported in a 32-bit BizTalk Host process.  
  
 **AS2 Decoder**  
  
 The AS2 Decoder is included in the decode stage of both the AS2EDIReceivePipeline and AS2Receive receive pipelines. It uses the BizTalk S/MIME Pipeline Component to provide S/MIME decoding functionality to AS2 and MDN messages.  
  
- Processes AS2/HTTP headers  
  
- Verifies the signature, if the message was signed  
  
- Decrypts the messages, if the message was encrypted (for an EDI/AS2 message, not an MDN)  
  
- Decompresses the message, if the message was compressed  
  
- Reconciles a received MDN with the original outbound message  
  
- Updates and correlates records in the non-repudiation database  
  
- Writes records for AS2 status reporting  
  
  > [!NOTE]
  >  If an error occurs during receive-side processing of an AS2 message, the AS2 Decoder will stop further downstream message processing (for example, the EDI disassembler will not parse the interchange). However, the AS2 Disassembler or EDI Disassembler must still generate the MDN.  
  
  > [!NOTE]
  >  Eight-bit encoding is used on AS2 messages. Base64 encoding is only applied to signatures in AS2 messages and MDNs.  
  
  **AS2 Disassembler**  
  
  In the AS2Receive receive pipeline, the AS2 Disassembler does the following:  
  
- Determines whether an MDN is required, and whether the MDN should be synchronous or asynchronous.  
  
- Generates an AS2 MDN.  
  
- If the MDN is synchronous, sets the `EdiIntAS.IsAS2AsynchronousMDN` property to False; if asynchronous, sets the property to True.  
  
- Sets the correlation tokens and properties on the MDN.  
  
  **EDI Disassembler**  
  
  In the AS2EDIReceivePipeline, the EDI Disassembler will parse the EDI message into intermediate XML message(s) for processing. For more information, see [How the EDI Disassembler Works](../core/how-the-edi-disassembler-works.md).  
  
  **BatchMarker**  
  
  In the AS2EDIReceivePipeline, the BatchMarker pipeline component sets the AgreementPartIdForSend and ToBeBatched context properties that are required for processing a batched interchange. This component is included in the last stage (agreement resolution) of the AS2EDIReceive pipeline. All pipelines that will batch EDI messages should include the BatchMarker pipeline component.  
  
> [!NOTE]
>  The BatchMarker pipeline component is not included in the AS2Receive pipeline that is used to process non-EDI messages. However, you can include the BatchMarker component in a custom receive pipeline that does not include the EDI Dissassembler. For more information, see "Processing Non-EDI Messages in the BatchMarker Component" in [Assembling a Batched EDI Interchange](../core/assembling-a-batched-edi-interchange.md).  
  
## HTTP Adapter  
 The receive ports and locations used for AS2 processing use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP Adapter. The HTTP Adapter is configured for either one-way and request-response transmission.  
  
## Non-Repudiation Database  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the non-repudiation database (the EdiMessageContent table of the BizTalkDTADb database) to do the following:  
  
> [!NOTE]
>  The EdiMessageContent table exists in the BizTalkDTADb database only if one of the non-repudiation storage agreement properties has been checked.  
  
-   Provides a non-repudiation trail for signed MDN  
  
-   Correlates an outbound message with its incoming MDN  
  
-   Stores messages through various state changes  
  
-   Associates error codes with HTTP Response and MDN  
  
-   Displays records based on filter criteria  
  
-   Archives marked records.  
  
> [!IMPORTANT]
>  To ensure authentication and integrity of messages stored in the non-repudiation receipt database, digital signatures should be used on all messages that will be stored in the database, both original AS2 messages and MDNs. For more information, see section 9.1 of [RFC 1430, "MIME-Based Secure Peer-to-Peer Business Data Interchange Using HTTP, Applicability Statement 2 (AS2)"](http://go.microsoft.com/fwlink/?LinkID=184212) ([http://go.microsoft.com/fwlink/?LinkID=184212](http://go.microsoft.com/fwlink/?LinkID=184212)).  
  
## See Also  
 [How BizTalk Server Receives AS2 Messages](../core/how-biztalk-server-receives-as2-messages.md)