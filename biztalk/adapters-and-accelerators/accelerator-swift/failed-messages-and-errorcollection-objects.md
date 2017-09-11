---
title: "Failed Messages and ErrorCollection Objects | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "failed messages, ErrorCollection objects"
  - "ErrorCollection objects"
ms.assetid: 8a2ff3b5-d7a0-4595-8b74-3133e9e3a821
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Failed Messages and ErrorCollection Objects
In addition to decorating a failed message with promoted properties, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] publishes the failed message to the MessageBox database with an additional message *part*, called **ErrorSegment**. This error part contains XML representing an **ErrorCollection** object. The A4SWIFT disassembler populates the **ErrorCollection** object during each stage of message processing (parsing, XML validation, and Business Rule Engine (BRE) validation).  
  
 The **ErrorCollection** object is a collection of *error objects*, each of which represents a particular error or failure during message processing. The individual error objects contain details about a single failure (such as the location in the message and a description of the failure).  
  
 For more information about the **ErrorCollection** application programming interface (API) and usage details, see ErrorCollection Class. For more information about individual error objects, see ErrorBase Class (the base class for error objects), BreValidationError Class, ParseError Class, and XmlValidationError Class.  
  
 This section contains:  
  
-   [Extending the Solution for Capture and Message Repair](../../adapters-and-accelerators/accelerator-swift/extending-the-solution-for-capture-and-message-repair.md)