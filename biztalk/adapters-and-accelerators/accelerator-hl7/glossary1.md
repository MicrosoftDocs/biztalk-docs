---
title: "Glossary for HL7 accelerator in BizTalk Server | Microsoft Docs"
description: Common terms and definitions to know and learn to use the BizTalk Accelerator for HL7
ms.custom: ""
ms.date: "08/16/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ffb9c18a-5fe5-448f-b115-0973e9d12952
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Glossary
Microsoft BizTalk Accelerator for HL7 uses the following terms and definitions.

## A    
 **artifact**    
 The artifacts that comprise the HL7 V3.0 ballot are the deliverables resulting from the discovery, analysis, and design activities leading to the creation of message specifications.  
  
 Within the HL7 V3.0 standards, the components that make up the documentation are artifacts. This includes storyboards, application roles, trigger events, Domain Message Information Model specifications (D-MIMs), Refined Message Information Model specifications (R-MIMs), Hierarchical Message Description specificatins(HMDs), message types, and interactions.  
  
 **artifact identifier**    
 A Technical Committee submits and gives each artifact a unique identifier that is assigned by concatenating the subsection, domain and artifact code, a 6-digit, non-meaningful number, a 2-digit Realm code, and a 2-digit version number.  

## C
  
 **cardinality**    
 The property of a data element (the number of times a data element may repeat within an individual occurrence of an object view) or column in the Hierarchical Message Description (the minimum and maximum number of occurrences of the message element). See Hierarchical Message Description.  
  
## D   
 **domain**    
 1. The problem or subject to be addressed by a set of HL7 messages or by a system ("application domain"). A particular area of interest in health care. 
 2. The set of possible values of a data type, attribute, or data type component. See vocabulary domain. 
 3. An interest group within HL7, such as Pharmacy, Laboratory, Patient Administration.  
  
## E 
 **event**    
 1. A stimulus that causes a noteworthy state change of an object. A signal that invokes the behavior of an object. See trigger event. 
 2. A vocabulary domain value for Mood.  
  
 
## H
**Hierarchical Message Description (HMD)**    
 A specification of the exact fields of a message and their grouping, sequence, optionality, and cardinality. Either contains message types for one or more interactions or represents one or more common message element types. This is the primary normative structure for HL7 messages.  
  
## M  
 **mandatory**    
 A column in the Hierarchical Message Description (HMD). If the inclusion for an attribute mandatory, all message elements based on this attribute must contain a non-null value, or they must have a default that is not null.  
  
  
 **message**    
 A package of information communicated from one application to another. See message type and message instance.  
  
 **Message Development Framework (MDF)**    
 The collection of models, methods, and tools that comprise the methodology for specifying HL7 V3.0 messages. Developers of the HL7 standards use this framework. The V3.0 Guide summarizes the content of the methodology.  
  
 **message element**    
 A unit of structure within a message type.  
  
 **message element type**    
 A portion of a message type that describes one of the elements of the message.  
  
 **message instance**    
 A message that is formatted for a specific transmission. The same message type can describe two messages  and identify with the same interaction and yet vary in the instance because of variations in values, presence, or absence of the data being sent and different cardinalities of collections. Otherwise, identical messages may be different instances if they are sent at different times or by a different sender.  
  
 **message payload**    
 Data carried in a message.  
  
 **message type**    
 The organization of message elements that is specified in a Hierarchical Message Description (HMD). Each message type is communicated as part of one or more interactions in the interaction model. A message type in effect constitutes a set of rules for constructing a message given a specific set of instance data. It also defines the rules for parsing a message to recover the instance data. The message type is independent of the Implementation Technology Specification, so that if the same data is sent using the same message type and different implementation technology specifications, the message type can be transliterated from one to the other.  

## P  
 **property**    
 Any attribute, association, method, or state model defined for a class or object. In an HMD, the column that states the name of the class, attribute, or association role name as it appears in the Reference Information Model (RIM).  

## R  
 **Reference Information Model (RIM)**    
 The HL7 information model from which all other information models (for example, R-MIMs) and messages derive.  
  
 **Refined Message Information Model (R-MIM)**    
 An information structure that represents the requirements for a set of messages. A constrained subset of the RIM that may contain additional classes that are cloned from RIM classes. Contains those classes, attributes, associations, and data types that are needed to support one or more Hierarchical Message Description (HMDs). A single message can be shown as a particular pathway through the classes within an R-MIM.  

## S  
 **scenario**    
 In Unified Modeling Language (UML), "a single path of execution through a single use case". A statement of events defined as a sequence of interactions relevant in health care. The scenario provides one set of interactions that the modeling committee expects to typically occur in the domain. Usually, a sequence diagram is constructed to show a group of interactions for a single scenario. Each scenario is displayed as a subset of the interaction model.  
  
 **schema**    
 1. A diagrammatic presentation, a structured framework, or a plan. 
 2. A set of requirements that need to be met in order for a document or set of data to be a valid expression within the context of that grammar. An XML schema is a specification in Standard Generalized Markup Language (SGML) of the structure of a document or set of data.

## Next steps
[Parties - BTAHL7 Configuration Explorer](parties-tab.md)  
[Global Settings - BTAHL7 Configuration Explorer](global-settings-tab.md)  
[MLLP Transport Properties Dialog Box UI Help](mllp-transport-properties-dialog-box-ui-help.md)