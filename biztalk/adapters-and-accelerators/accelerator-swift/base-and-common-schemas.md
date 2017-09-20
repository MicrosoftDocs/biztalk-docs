---
title: "Base and Common Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "base schemas"
  - "schemas, common schemas"
  - "schemas, base schemas"
  - "common schemas"
ms.assetid: 60eb24f6-cc4f-4c6d-ab15-9e3a6b4ed376
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Base and Common Schemas
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] has implemented the records and elements that comprise individual message schemas in separate schemas. This approach provides a single location to provide updates for fields and formats, insulating the message schema from such changes.  
  
 The base schema (**SWIFT Base Types.xsd**) contains the common record and element definitions that the message schemas reference. The common record and element definitions correspond to the SWIFT FIN message fields. You need to add this schema to any project that uses the message schema. The base schema covers the rules and common functions, and defines the formats that A4SWIFT uses to validate the appropriate message instances. The SWIFT Base Types.xsd schema defines XSD **simpleType** and complex elements for SWIFT fields. SWIFT has defined **simpleType** elements for all base fields, such as the Amount, Rate, Price, and so on, which SWIFT uses in many of the fields. The SWIFT Base Types.xsd schema also defines XSD complex elements for fields that include many of the custom **simpleTypes** defined in the schema. For example, the **BankIdentifierCode** complex element uses Bank Code, Country Code, Area Code, and Branch Code. Users can add new **simpleTypes** and complex elements that mirror SWIFT fields and can modify existing types. You should take care, however, when you modify existing types, because the Business Rule Engine (BRE) Validation and XML Validation features are dependent upon these defined types.  
  
 The common schema (**SWIFT Common Data Types.xsd**) defines the character sets appropriate to the fields in the base schema. SWIFT defines these character sets, as referenced in the *SWIFT User Handbook*. You also need to add the common schema to your schema projects.  
  
## See Also  
 [Working with Schemas](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)