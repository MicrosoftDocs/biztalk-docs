---
title: "BTARN Receive Pipeline | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BTARN, receive pipelines"
  - "RNMimeDecoder component"
  - "ReceiveMessageNonRepudiate component"
  - "RNDAsm component"
  - "receive pipelines, message flow"
  - "RNPartyRes component"
  - "receive pipelines, BTARN"
  - "MessageUpdater component"
  - "messages, message flow"
ms.assetid: 811f2a6a-ddd2-49cc-a00b-4c9d0110a0d1
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BTARN Receive Pipeline
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] performs RosettaNet Implementation Framework (RNIF) message reception with the RNIFReceive pipeline (RNIFReceive.btp). The receive pipeline includes the following components:  
  
-   ReceiveMessageNonRepudiate  
  
-   RNMimeDecoder (MIME Preprocessor/Decoder)  
  
-   RNDAsm (XML Disassembler)  
  
-   RNPartyRes (Party Resolution component)  
  
-   MessageUpdater  
  
## ReceiveMessageNonRepudiate  
 This component stores the received message in the MessageStorageIn table. This component performs the non-repudiation processing required by the RNIF standards.  
  
## RNMimeDecoder  
 This component is based on the native BizTalk Server MIME Preprocessor/Decoder. RNMimeDecoder adds the following functionality for RNIF processing:  
  
- For RNIF 2.01, decrypts the service content and attachments, if they are present.  
  
- For RNIF 1.1, handles the 8-byte header and the detached signature header at the end of the payload.  
  
  For more information about the native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] preprocessor/decoder, see "MIME/SMIME Decoder Pipeline Component" in BizTalk Server Help.  
  
## RNDAsm  
 This component is based on the native BizTalk Server XML Disassembler. RNDAsm adds the following functionality for RNIF processing:  
  
- If an incoming document has a DOCTYPE header, this component generates a namespace from it and moves all nodes in the incoming document to that namespace.  
  
- Performs message correlation to determine whether an incoming message is a duplicate, and generates an error message if the message is a duplicate.  
  
- Stores attachments as additional parts of the message.  
  
- Promotes message properties.  
  
  For more information about the native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Disassembler, see "XML Disassembler Pipeline Component" in BizTalk Server Help.  
  
## RNPartyRes  
 This component is based on the native BizTalk Server Party Resolution component. RNPartyRes adds the following functionality for RNIF processing:  
  
- Maps the sender certificate if the incoming message is signed to a BizTalk party. If the incoming message is not signed, and the trading partner agreement allows for it, this component retrieves the sender party from the Delivery header for RNIF 2.01 or the Service header for RNIF 1.1.  
  
- Validates that the sender exists and that the sender has a trading partner agreement with the home organization.  
  
  For more information about the native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] party resolution component, see "Party Resolution Pipeline Component" in BizTalk Server Help.  
  
## MessageUpdater  
 This component adds the following functionality for RNIF processing:  
  
-   Updates the MessageStorageIn table with details about the PIP Code, PIP Version, Source Party, Destination Party, and Message Tracking ID of the wire message that was stored by the ReceiveMessageNonRepudiate component.  
  
-   If the PIP does not require non-repudiation, marks the record for deletion, setting `ToBePurged = True`.  
  
## Message Flow  
 The message flow through the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] receive pipeline is as follows:  
  
1. The HTTP adapter receives an RNIF 1.1 object or an RNIF 2.01 business message through HTTP POST.  
  
2. If the adapter successfully receives the message, the adapter extracts the RosettaNet object or business message, and routes it to the receive pipeline.  
  
3. If the object or business message is signed, the MIME Preprocessor/Decoder removes the signature.  
  
4. If the signature is valid, the disassembler reads the preamble.  
  
5. If the message is an action message, and non-repudiation is required (the **Non-Repudiation of Origin and Content** setting in the process configuration settings is `True`), the Decoder calculates and persists the digest.  
  
6. The disassembler validates the preamble (with message (MSG) guidelines and the preamble schema in the global variables).  
  
7. For RNIF 2.01, the disassembler reads the delivery header, and validates the header using the MSG guidelines and the delivery header schema in the global variables.  
  
8. For RNIF 2.01, the disassembler extracts the partner information from the delivery header, and examines the signature to verify that it belongs to the partner.  
  
9. For RNIF 2.01, if the payload is encrypted, the decoder decrypts the payload container.  
  
10. The disassembler reads the service header, and validates the header using the MSG guidelines and the service header schema in the global variables.  
  
11. For RNIF 1.1, the disassembler extracts the partner information from the service header, and examines the signature to verify that it belongs to the partner.  
  
12. The disassembler checks whether the partner is authorized for the PIP. If not, the disassembler will reply an HTTP POST with an HTTP 403 status message, if necessary, and post an error.  
  
13. If the message is a signed action message and **Non-Repudiation of Origin and Content** is set to `True`, the ReceiveMessageNonRepudiate component persists the original message in the MessageStorageIn table.  
  
14. If the message is a signed signal message and **Non-Repudiation Required** is set to `True`, the ReceiveMessageNonRepudiate component persists the signal message in the MessageStorageIn table.  
  
15. If the message was persisted in the MessageStorageIn table for non-repudiation, the MessageUpdater updates the MessageStorageIn table with properties of the process configuration of the message.  
  
16. If the message is an action message that is a duplicate of a previously processed action message, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will post an error.  
  
17. For RNIF 2.01, the decoder will decrypt the payload if the action message is encrypted and there is a match between the HTTP synchronicity and PIP synchronicity requirements.  
  
18. The disassembler reads the service content, and validates it using the MSG guidelines and the schema.  
  
19. For RNIF 2.01, the disassembler verifies that the manifest is valid and the content ID is present.  
  
20. For RNIF 2.01, the disassembler will read any attachments.  
  
21. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] routes the RosettaNet headers, service content, and attachments to the public process.  
  
## See Also  
 [Message Processing in BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)