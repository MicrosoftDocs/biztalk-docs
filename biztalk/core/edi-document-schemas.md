---
title: "EDI Document Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc3a30b8-0686-4c06-985b-13f2c95f8e99
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EDI Document Schemas
Document schemas define the body of an EDI transaction document type.  
  
## Schema Delivery and Setup  
 EDI document schemas are delivered in a compressed state in a self-extracting executable, [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\MicrosoftEdiXSDTemplates.exe. The self-extracting executable ensures that an appropriate folder structure is created (per the encoding type and version/release sub types). When executed, the executable deposits EANCOM, EDIFACT, HIPAA, and X12 schemas into subfolders in the same directory as the executable.  
  
 The default schema namespaces are:  
  
-   For X12 – `http://schemas.microsoft.com/BizTalk/EDI/X12/2006`  
  
-   For EDIFACT – `http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006`  
  
## Schema Naming Convention  
 The naming convention for the X12 and EDIFACT encoding type is \<Encoding\>*\<Version\>\<Release\>\\*\<Doctype\>. Examples are the X12_00401_864.xsd schema for the X12 864 document type (version 004, release 01) and the EDIFACT_D01C_AUTHOR.xsd schema for the EDIFACT AUTHOR document type (version D01, release C).  
  
> [!NOTE]
>  The schema name of an EDIFACT schema is case-sensitive. For example, EFACT_D98B_ORDERS and EFACT_d98B_Orders would be two different schemas.  
  
## Schema Contents  
 A document schema starts with the ST transaction set header and ends with the SE transaction set trailer for an X12-encoded document. It starts with the UNH message header and ends with the UNT message trailer for an EDIFACT-encoded document. The schema defines each data element of these headers and trailers.  
  
 A document schema then defines each segment within the transaction set/message and the data elements within those segments. For example, the X12_00401_864.xsd schema defines the BMG01, BMG02, and BMG03 elements of the BMG segments. The schema specifies the characteristics of the segment's complex data type, such as the field order, delimiter type, and namespace. If there are cross-field validation rules for the segment, the schema defines the rules. For more information, see [Cross Field-Segment Validation](../core/cross-field-segment-validation.md).  
  
 The schema specifies the characteristics of each data element within the segment, such as the simple data type, minimum occurrences, minimum length, and maximum length.  
  
 If there is a loop in the message type, the schema defines the data elements within each loop, the minimum and maximum occurrences of the loop, and whether the loop is bounded or unbounded. The schema also defines nesting of a segment, and whether the loop is explicit or implicit.  
  
## See Also  
 [EDI Message Structure](../core/edi-message-structure.md)   
 [EDI Message Validation](../core/edi-message-validation.md)