---
title: "Vocabularies | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "business rules, vocabularies"
  - "vocabularies, about vocabularies"
  - "vocabularies"
  - "Business Rules Engine, vocabularies"
ms.assetid: 591673a0-2c4d-41ca-9997-b363c086dd66
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Vocabularies
The terms used to define rule conditions and actions are usually expressed by domain or industry-specific nomenclature. For example, an e-mail user writes rules in terms of messages "received from" and messages "received after," while an insurance business analyst writes rules in terms of "risk factors" and "coverage amount."  
  
 Underlying this domain-specific terminology are the technology artifacts (objects, database tables, and XML documents) that implement rule conditions and rule actions. Vocabulariesare designed to bridge the gap between business semantics and implementation.  
  
 For example, a data binding for an approval status might point to a certain column in a certain row in a certain database, represented as an SQL query. Instead of inserting this sort of complex representation in a rule, you might instead create a vocabulary definition, associated with that data binding, with a friendly name of "Status." Subsequently you can include "Status" in any number of rules, and the rule engine can retrieve the corresponding data from the table.  
  
 A *vocabulary* is a collection of definitions consisting of friendly names for the facts used in rule conditions and actions. Vocabulary definitions make the rules easier to read, understand, and share by people in a particular business domain.  
  
 You can use the Business Rule Composer to define vocabularies that are then placed in the shared rule store. Vocabularies can also be consumed by tool developers responsible for integrating rule authoring into new or existing applications.  
  
 Before you can use a vocabulary, it must be stamped with a version and published in your rule store. This is to guarantee that the definitions in the vocabulary will not change, and to preserve referential integrity. This means that any policies that use that particular version of the vocabulary will not fail unexpectedly due to changes in the underlying vocabulary.  
  
## See Also  
 [Business Rules Engine](../core/business-rules-engine.md)