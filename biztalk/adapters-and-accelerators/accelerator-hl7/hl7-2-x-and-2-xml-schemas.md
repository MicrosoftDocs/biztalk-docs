---
title: "HL7 2.X and 2.XML Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "schemas, schema types"
  - "HL7-encoded messages"
  - "2.X schemas"
  - "schemas, HL7 organization"
  - "BTAHL7, HL7 schemas"
  - "HL7, 2.XML schemas"
  - "Update2XMLSchema tool"
  - "schemas, common schemas"
  - "2.X schemas, about 2.X schemas"
  - "2.X schemas, compatibility"
  - "2.XML schemas, compatibility"
  - "messages, HL7-encoded messages"
  - "HL7 Schema Selector"
  - "schemas, 2.XML schemas"
  - "2.XML schemas"
  - "2.XML schemas, about 2.XML schemas"
  - "HL7, 2.X schemas"
  - "schemas, compatibility"
  - "common schemas"
  - "schemas, 2.X schemas"
ms.assetid: 02532d72-1948-48d8-a8ef-6b5a814eb573
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HL7 2.X and 2.XML Schemas
The HL7 organization publishes two sets of schemas: HL7 2.X schemas, used for HL7-encoded messages, and HL7 2.XML schemas, used for XML-encoded messages.  

 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] works natively with the HL7 2.X schemas. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] setup loads the HL7 2.X schema files into \<*drive*\>:\program files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for HL7\Templates\Schemas\2.X. As a result, the HL7 2.X schemas are available in the HL7 Schema Selector. You run the HL7 Schema Selector in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  

 BTAHL7 works with the HL7 2.XML schemas, but the BTAHL7 setup program does not load the HL7 2.XML schemas with the BTAHL7 program files, and you have to modify some of the HL7 2.XML schemas for them to work with BTAHL7. To make them available in the HL7 Schema Selector and make the required modifications, download the 2.XML schemas from the HL7 organization Web site, and then run the **Update2XMLSchema** tool (for more information, see [Update2XMLSchema Tool](../../adapters-and-accelerators/accelerator-hl7/update2xmlschema-tool.md)). The tool will modify the HL7 2.XML schemas as required to work with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], and then place them in \<*drive*\>:\program files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for HL7\Templates\Schemas.  

 Each of these sets of schemas includes a series of versions. HL7 2.X live schema versions include 2.1 through 2.5 (for more information, see [HL7 Versions](../../adapters-and-accelerators/accelerator-hl7/hl7-versions.md)). HL72.XML schema versions include 2.3.1, 2.4, and 2.5. HL7 2.X schema versions are backward compliant. HL7 2.XML schema versions are not backward compliant.  

> [!NOTE]
>  Because version 2.4 of 2.XML is not backward compliant with 2.3.1 for 2.XML, an error may occur if you deploy a 2.4 version of the 2.XML schema, and then submit an instance of a message conforming to the 2.3.1 version. To correct this, you may need to create a different target namespace to deal with 2.3.1 messages.  

 When you create a multi-part HL7 2.X message, you must set the type of the body part to a specific schema. If not, the serializer will reject the message.  

 The following table describes the two basic types of schemas with which BTAHL7 works.  


|            Schema Type            |                                                                                                                                                                                                                                                                                                   Description                                                                                                                                                                                                                                                                                                    |
|-----------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| HL7FF – ER7 Encoded (2.X) Schemas | BTAHL7 provides HL7 2.X schemas derived from the HL7 Access database, including:<br /><br /> -   A set of all specific schemas based on version, message type, or event<br />-   Common schemas for segments, data types, tables, headers, and acknowledgments (ACKs)<br /><br /> BTAHL7 supports the following schema templates:<br /><br /> -   V2.1<br />-   V2.2<br />-   V2.3<br />-   V2.3.1<br />-   V2.4<br />-   V2.5<br /><br /> BTAHL7 setup installs V2.X schemas in \<*drive*\>\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7\Templates\Schemas. |
|      HL7XML – 2.XML Encoding      |                                                                                                                                            BTAHL7 supports the following schemas:<br /><br /> -   V2.3.1<br />-   V2.4<br />-   V2.5<br /><br /> BTAHL7 setup does not install the 2.XML schemas. To install them and modify them to work with BizTalk Editor, see [Update2XMLSchema Tool](../../adapters-and-accelerators/accelerator-hl7/update2xmlschema-tool.md).                                                                                                                                            |

## Common Schemas  
 BTAHL7 uses an HL7 schema specific to a message type to create and validate the body of an instance of that message type. It also uses common schemas, in addition to the specific schemas. BTAHL7 uses common HL7 schemas to validate HL7 message headers and acknowledgments. These files are MSH_25_GLO_DEF.xsd for headers and ACK_24_GLO_DEF for acknowledgments.  

 BTAHL7 also uses common schemas to validate data types, segments, and table values. These schemas are specific to each version of the HL7 standards. For instance, the common schemas for V2.2 messages are datatype_22.xsd, segments_22.xsd, and tablevalues_22.xsd. BTAHL7 uses these schemas to validate data types, segments, and table values for all V2.2 messages.  

## See Also  
 [Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [BTAHL72X Flat File Processing](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md)   
 [BTAHL72XML Processing](../../adapters-and-accelerators/accelerator-hl7/btahl72xml-processing.md)   
 [Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)   
 [Using HL7 2.XML Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)