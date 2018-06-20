---
title: "SWIFT Header and Trailer Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "trailer schemas"
  - "schemas, headers"
  - "schemas, trailers"
  - "header schemas"
ms.assetid: 82cd33d4-6bbb-4124-9506-fd35b5dca8a4
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SWIFT Header and Trailer Schemas
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provides the SWIFT header and trailer schemas. A4SWIFT has already incorporated these into the interchange schemas for the various FIN messages. If you want to create a custom SWIFT FIN format style message type (for example, an N98 message), you can incorporate the header and trailer schemas into your own format.  
  
 The SWIFT header schema (SWIFT Header.xsd) contains the formats for the following:  
  
- Basic Header  
  
- Application Header (choice of Input or Output)  
  
- User Header  
  
- Beginning delimiter of the text block  
  
  The Basic Header contains information about the source of the message. The Application Header contains information about the message type and the destination of the message. The resolution of the message type by the SWIFT disassembler in a receive pipeline is based upon the contents of the field in the appropriate Application Header. The User Header is optional, and contains special processing instructions.  
  
> [!NOTE]
>  A few message types have variable formats based upon the contents of field 119 in the User Header. These are "dual message types" in A4SWIFT. The A4SWIFT disassembler uses the message type in the Application Header in conjunction with the contents of field 119 to select the appropriate schema for a message instance.  
  
 The *SWIFT User Handbook*, which is part of the SWIFT documentation for the FIN service, describes all of these headers.  
  
 The beginning of the text block is "{4:" followed by a carriage return and line feed. The beginning of the text block is required.  
  
 In order to accommodate processing (parsing and validation) of interchanges containing only SWIFT block 4, all header and trailer blocks in the interchange schemas are marked as optional. This deviates from the SWIFT FIN specification, where the Basic Header block 1 and the Application Header block 2 are mandatory. This enables you to use the interchange schema to handle messages that do not require headers. For example, if you are accepting messages received through FileAct, the batch header may contain the source of the messages as well as a common message type.  
  
 The RunTime schema DLL also includes the header schema. A4SWIFT installation deploys the RunTime schema DLL and the A4SWIFT property schema. If you need to use your own header for processing, you can define and deploy a custom header schema, and promote the appropriate properties for message resolution. If you do so, you will also need to specify the new header to the SWIFT disassembler (DASM). The custom header schema should not have the same Document Type as the SWIFT header schema that A4SWIFT installation has deployed in the RunTime schemas DLL. Be sure to change the schema namespace, or root node name, or both.  
  
 The SWIFT Trailer schema (**SWIFT Trailer.xsd**) contains the format for the following:  
  
- Ending delimiter of the text block  
  
- User trailers (user and system information)  
  
- System trailers  
  
  The ending delimiter of the text block is "-}". The trailer block begins with "{5:". The contents of the trailer block include both user information (checksum, message authentication, proprietary authentication, and so on) and system information (delayed message, message reference, possible duplicate message, and so on). Trailers added by SWIFT also provide a third block, delimited by "{S:". The *SWIFT User Handbook*, under "FIN Service Description", describes in detail the contents of block 5. A4SWIFT does not validate the contents of block S.  
  
  The actual FIN interface or the SWIFT network appends the trailers. If a message contains a trailer when A4SWIFT receives the message, A4SWIFT carries the trailer with the message. A4SWIFT does not raise an error if a message does not contain a trailer when A4SWIFT receives the message. As with headers, all of the trailer entries, including the blocks themselves, are optional in A4SWIFT.  
  
## See Also  
 [Working with Schemas](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)