---
title: "Working with Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "developing, schemas"
  - "schemas, developing"
ms.assetid: 123c4b43-34e4-41c7-980d-5d518b1479c1
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Working with Schemas
The schemas provided in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] are the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] XSD representation of the Society for Worldwide Interbank Financial Telecommunication (SWIFT) FIN messages. Each message type has its own schema, including the SWIFT header and SWIFT trailer (interchange format). This schema is sufficient to send or receive a SWIFT message. These schemas are a unique mixture of delimited and positional records, providing a detailed XML representation of the flat-file FIN structures.  

 Most SWIFT customers use a relatively small subset of the SWIFT FIN messages. To implement a solution for these customers, you can create a BizTalk schema project (as demonstrated in [Module 2: Adding a New Schemas Project](../../adapters-and-accelerators/accelerator-swift/module-2-adding-a-new-schemas-project.md) of the A4SWIFT tutorial). Add the relevant message schemas (MT*xxx*.xsd) from \\\ Program Files\Microsoft BizTalk Accelerator for SWIFT \<version\> MessagePack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category x\MT xyy directory, where x is the first digit of the FIN message type and xyy is the three-digit message type for the message.  

 You can add several schemas to the same project. To maintain manageability, you should not add more than 20 message schemas per project. You also need to add the base and common schemas to the project. If you have already deployed the base and common schemas, you need to make a reference to their assembly, rather than deploy them. This section describes these schemas. The message schemas are ready to use as is for both messages sent to the SWIFT network and messages received from SWIFT.  

 You can examine the contents of each SWIFT schema in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] using the Schema Editor. All of the message interchange schemas have the following common structure:  

- Headers  

- Message text  

- Trailers  

  This section describes the header and trailer schemas. The message text comprises the payload of the FIN message, and contains all of the data fields except the fields containing the sender, receiver, and message type. These three fields are contained in the header portion. Some messages also contain an optional user header, which may also provide processing information.  

  Each FIN message payload consists of a series of fields in a defined sequence. These fields conform to the following rules:  

- The fields may be required or optional within the sequence.  

- A sequence may contain sub-sequences, and a sub-sequence may repeat within a sequence.  

- You can use a field in several message types.  

- Within a field, there may be elements or subfields. An element or subfield may be common to several fields.  

- A group node represents each repeating sequence.  

- Each field may itself have multiple nodal levels, each described as a record.  

- Schema elements represent only the lowest level subfields.  

- The common and base schemas define common records and elements.  

- Schemas represent some fields in several formats (such as party fields). Schemas define such fields as choice fields.  

- Some fields have limited sets of values. For the most part, the schema lists these values. Schema definitions also include character set validation.  

  This section contains:  

- [Base and Common Schemas](../../adapters-and-accelerators/accelerator-swift/base-and-common-schemas.md)  

- [SWIFT Header and Trailer Schemas](../../adapters-and-accelerators/accelerator-swift/swift-header-and-trailer-schemas.md)  

- [SWIFT Schema Naming Conventions](../../adapters-and-accelerators/accelerator-swift/swift-schema-naming-conventions.md)
