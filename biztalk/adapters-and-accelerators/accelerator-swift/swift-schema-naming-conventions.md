---
title: "SWIFT Schema Naming Conventions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "naming conventions [schemas]"
  - "schemas, naming conventions"
ms.assetid: 3c1f2519-2575-4178-89c1-e97333c1e6bd
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SWIFT Schema Naming Conventions
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] includes schemas for Society for Worldwide Interbank Financial Telecommunication (SWIFT) FIN messages that were created using BizTalk Editor. These schemas conform to the following conventions throughout:  
  
> [!NOTE]
>  All schemas are versioned. To see the version, open [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], and right-click the schema in Solution Explorer. With the \<Schema\> node selected in BizTalk Editor, in the Properties pane scroll down to the Standard Version property.  
  
- The name of each interchange schema file is **MT*xxx*.xsd**, where *xxx* is the FIN message type.  
  
- The name of the associated master policy file for each message is **MT*xxx*_Master_Policy.xml**, and the corresponding name in the Business Rule Engine (BRE) is **MT*xxx*_Master_Policy**, with a list name of **MT*xxx*_PolicyList**.  
  
- The name of the associated validation policy file for each message is **MT*xxx*_Validation_Policy.xml**, and the corresponding name in the BRE is **MT*xxx*_Validation_Policy**.  
  
- Within each message schema, the name of the root is **SWIFT_CATEGORY*z*_MT*zxx*_Interchange**, where *z* is the message category (first digit of the message type) and *zxx* is the message type.  
  
- The target namespace for each message schema is **<http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/Category*z*/MT*zxx>**<em>, where *z</em> is the message category (first digit of the message type) and *zxx* is the message type.  
  
- The document type is **MT*zxx**<em>, where *zxx</em> is the message type.  
  
- The names of fields that are not numbered and sub-fields include descriptive business names. The first letter of each word is capitalized, and the names do not include an intervening space or punctuation between words (for example, the name would be **ServiceIdentifier**, not **Service Identifier**).  
  
- The labels of sequences within messages conform to the *SWIFT Reference Guide* (for example, **SequenceA**).  
  
- The labels of numbered SWIFT fields include a descriptive title followed by the sequence (if present), followed by the number code and optional letter format (for example, **Reference_A_20C**).  
  
- Where there is a choice of multiple formats for a field, the label of the node is **\<*Choice*\>**, and then each option is a numbered field (for example, **Date_A_98A** and **DateTime_A_98C**).  
  
- The name of the lowest level element definition of a sub-field consists of the name of the sub-field followed by **Type** (for example, **accountType** for Account).  
  
  Other namespaces in the message schema include the following:  
  
- xmlns:xs="<http://www.w3.org/2001/XMLSchema>". This is the default W3C XML Schema namespace.  
  
- xmlns:b="<http://schemas.microsoft.com/BizTalk/2003>". This is the default BizTalk namespace.  
  
  Each message schema directly references the base type and common data type schemas.  
  
## See Also  
 [Working with Schemas](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)