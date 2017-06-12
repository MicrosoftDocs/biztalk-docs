---
title: "Message Validation Engine | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "message validation engine"
  - "errors, validating"
  - "XML validation"
  - "parsing validation"
  - "BRE policies, validating"
  - "errors, messages"
  - "messages, errors"
  - "validating, messages"
  - "validating, BRE policies"
  - "validating, XML"
  - "messages, validating"
  - "validating, errors"
  - "validating, parsing"
ms.assetid: 4ba0b75e-665b-4771-b04f-5bc3e90d83f0
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Validation Engine
One of the most important features provided by [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] is the ability to fully validate SWIFT messages received from back-end systems destined for the SWIFT network, or received from the SWIFT network (sent by trading partners). Validating outbound SWIFT messages guarantees that the messages conform to SWIFT standards and that the SWIFT network will not reject the messages.  
  
 Validating inbound SWIFT messages ensures that messages received from other financial institutions obey particular agreements (business rules) specific to the relationship. In both scenarios, the ability to validate and trap errors before committing a message helps to reduce transaction costs and total cost of ownership (TCO).  
  
 The following list describes the four parts that make up the A4SWIFT validation engine:  
  
-   Structural validation performed by the flat file parser  
  
-   Data validation performed by the XML validating reader  
  
-   SWIFT network and usage rule validation performed by the Business Rule Engine (BRE)  
  
-   Message marking and "best effort" error collecting  
  
## Structural Validation (Parsing)  
 A4SWIFT parses SWIFT flat file messages against XSD schemas defined for each SWIFT message type in accordance with the SWIFT standard. Parsing a flat file into XML guarantees that the flat file is structurally correct. Parsing also produces XML that is easier to read, manipulate, or transform into other formats or message types. You can also validate the XML against schema for data validity and use the Business Rule Engine (BRE) for more complex evaluations.  
  
 The SWIFT disassembler invokes the BizTalk flat file parser to parse SWIFT flat file messages invoked by the SWIFT disassembler. The SWIFT disassembler records in an error collection the details of any errors encountered during parsing, and always attempts to continue parsing the data in an effort to collect as many structural errors as possible on the first pass. However, most parse errors are fatal and halt message processing at the first error.  
  
 For more information about structural validation, see [Working with Schemas](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md).  
  
## Data Validation (XML Validation)  
 You can define SWIFT messages that pass structural validation as well-formed XML conforming to defined XSD schemas. A4SWIFT produces XML for structurally valid SWIFT messages during the parsing stage. A4SWIFT can then validate this XML for data correctness against constraints defined in the corresponding XSD schema.  
  
 These constraints include data typing, length, and value ranges defined in accordance with the SWIFT standard. The SWIFT disassembler invokes the XML validating reader to perform data validation.  
  
 The SWIFT disassembler records in an error collection the details of any errors encountered during XML validation, and continues validating the remaining data to collect as many XML validation errors as possible on the first pass. (Unlike parsing, continuation of XML validation is guaranteed.)  
  
 For more information about data validation, see [Working with Schemas](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md).  
  
## SWIFT Network and Usage Rule Validation (BRE Validation)  
 A4SWIFT validates XML for structurally valid SWIFT messages for business-level correctness against Business Rule Engine (BRE) policies. These policies include enforcement of SWIFT network and usage rules and other complex cross-field rules defined in accordance with the SWIFT standard. The SWIFT disassembler invokes the BRE to perform business-level validation.  
  
 The SWIFT disassembler records in an error collection the details of any errors encountered during BRE validation, and continues validating the remaining data to collect as many BRE validation errors as possible on the first pass. (Like XML validation, continuation of BRE validation is guaranteed.)  
  
 For more information about SWIFT network and usage rule validation, see [Working with BRE Policies](../../adapters-and-accelerators/accelerator-swift/working-with-bre-policies.md).  
  
## Validation Failures and Message Marking  
 A4SWIFT collects validation errors and details through each stage of message validation: structural parsing, XML validation, and BRE validation. A4SWIFT collects these errors using a "best effort" heuristic to gather as much error information about a message as possible. This functionality allows a failing message to have all errors caught and reported in one pass rather than having multiple iterations of submit, validate, fail, fix, resubmit.  
  
 Messages that have at least one error encountered during any validation stage in the error collection are considered invalid and are failed. A4SWIFT publishes these messages to the MessageBox database, but they are marked with promoted properties to indicate that the message has failed validation and to report error counts for each validation stage.  
  
 In addition to the promoted properties, A4SWIFT serializes the error collection into XML and attaches the collection as an "error part" of the multipart message. The final message consists of the failed message in the body part and error-collection XML in the error part, and is enhanced with A4SWIFT promoted properties that indicate a failure state. The SWIFT disassembler publishes this multipart message to the MessageBox database.  
  
 BizTalk send ports or orchestrations can retrieve failed messages from the MessageBox database by subscribing to the special A4SWIFT promoted properties. You can make subscriptions to retrieve all failed messages or only messages with a particular number of errors from specific validation stages.  
  
 After a failed message is retrieved, you can send it to a reporting application, a repair application or process, or a failure repository, or you can discard it.  
  
 This ability to subscribe to failed messages (and to differentiate between types of failures in the subscription), coupled with information-rich error collection XML attached to each failed message, forms a powerful framework for developing simple error reporting applications, such as provided by the message repair and new submission feature installed by A4SWIFT setup.  
  
 For more information about validation failures and message marking, see [Working with Failed Message Subscriptions](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md).  
  
## See Also  
 [BizTalk Accelerator for SWIFT Runtime](../../adapters-and-accelerators/accelerator-swift/biztalk-accelerator-for-swift-runtime.md)