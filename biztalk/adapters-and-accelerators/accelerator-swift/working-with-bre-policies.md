---
title: "Working with BRE Policies | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BRE policies, about BRE policies"
  - "BRE policies"
ms.assetid: 4470f2b3-6891-46d7-9ba1-848f90d0767d
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Working with BRE Policies
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] validates SWIFT messages by using Business Rule Engine (BRE) polices, as described in the *SWIFT Reference Guide*. These policies include the following:  

- Formatting  

- Value range  

- Valid list entries  

- Network rules with corresponding error codes  

- Usage rules that can be validated from the message content  

  These policies do not include general practices that are not dependent on the message content, or any cross-message validations.  

  The XSD schema for the message (and header and trailer) implements basic field optionality and cardinality, while the message schema that implements formatting references the SWIFT Base Types.xsd schema. Two specific policies for each message type define the rules associated with each message:  

- Master policy (MT*xxx*_Master_Policy.xml)  

- Validation policy (MT*xxx*_Validation_Policy.xml)  

  The master policy for each message type invokes the specific policies that apply to that message type. These specific policies include special field checks that common functions implement, network rules, and usage rules. The master policy for the message is the first policy run for that message. The list of policies includes the validation policy for the message type. Each master policy has the construct "if this message type, then run the list of policies".  

  The validation policy for each message type lists the single-field checks that other external rules implement, such as field codes, or uses a specific vocabulary for the field. These individual rules are generally common across two or more messages, because they are field-specific. The A4SWIFT_Codelists in the BRE vocabulary, not programming code, provide the allowed field values.  

  The *SWIFT Reference Guide* implements each of the network rules independently. Each network rule addresses the set of message types that the *SWIFT Reference Guide* defines.  

  A4SWIFT Setup does not install rules when it installs A4SWIFT. After you select the schemas, and build and deploy an assembly, you can use the BRE Deployment Utility to select and deploy the appropriate rules for the schema set. To deploy the rules for the selected messages, run the utility and select the relevant assemblies. The tool selects the corresponding master policies, validation policies, and any referenced network or other rules.  

  A4SWIFT associates two types of vocabularies with A4SWIFT rules. The first vocabulary is A4SWIFT_Codelist, which contains the various code-list values. The second vocabulary is A4SWIFT_Functions. These vocabularies are [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] classes for logic validations and calculations.  

  You can invoke the rules by the A4SWIFT disassembler in a receive pipeline, by setting the BRE validation configuration parameter to true. You can also invoke the rules from an orchestration. You cannot invoke the rules by the A4SWIFT assembler (ASM). You must use an orchestration or receive pipeline to validate the instance against the schema and invoke the rules.  

  If a message fails either schema validation or a business rule, A4SWIFT prepares an error collection that contains a description of the errors found and an indication of the field in error or the position in the message where the error occurred. For more information, see [Working with Failed Message Subscriptions](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md).  

  You can add additional rules to the set that A4SWIFT provides. For example, if you adopt a market practice group rule that affects a new set of messages, you can implement a new version of the master policy that includes one or more new validations, as required. Similarly, if you impose additional single-field checks, you can add these checks to a new version of the message validation policy. You can implement the new validation as a new rule or as a vocabulary function.  

  This section contains:  

- [Enabling Validation of Bank Identifier Codes](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md)  

- [Managing the Bicplus Table in the A4SWIFT Database](../../adapters-and-accelerators/accelerator-swift/managing-the-bicplus-table-in-the-a4swift-database.md)  

- [Supporting Leading Zeros in Amount Field Validations](../../adapters-and-accelerators/accelerator-swift/supporting-leading-zeros-in-amount-field-validations.md)  

- [Setting Offsets for Amount Validation](../../adapters-and-accelerators/accelerator-swift/setting-offsets-for-amount-validation.md)  

- [Removing Usage Rule Validation](../../adapters-and-accelerators/accelerator-swift/removing-usage-rule-validation.md)
