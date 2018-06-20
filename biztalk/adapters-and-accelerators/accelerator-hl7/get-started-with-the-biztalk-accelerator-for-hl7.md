---
title: "Get started with the BizTalk Accelerator for HL7 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "btahl7.configurationexplorer.gettingstarted"
helpviewer_keywords: 
  - "BizTalk Accelerator for HL7"
  - "BizTalk Accelerator for HL7, getting started"
  - "getting started"
ms.assetid: e842d501-2037-4fd6-a518-d29b25877250
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Get started with the BizTalk Accelerator for HL7
Using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef_md](../../includes/hl7-currentversion-firstref-md.md)], you can develop business processes between your health care computer systems. By using [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)], developers, IT professionals, and interface analysts can work in a common environment to develop end-to-end integrated BTAHL7-based solutions across health care applications.  
  
 More specifically, with [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] you can:  
  
- **Simplify health care application integration**. Build, manage, and track distributed business processes using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] development environment.  
  
- **Standardize clinical data interchange between medical applications**. Transform existing data transmission between applications to the [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] standard.  
  
- **Increase efficiency**. Automate all communication processes between medical applications with minimal manual intervention.  

This section provides role-specific information about how you can use [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] and [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] to facilitate Enterprise Application Integration (EAI) within hospitals and the healthcare arena to automate business-to-business healthcare solutions.  
  
[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] provides four separate scenarios in tutorial format for each type of solution. Before you begin these tutorials, you should understand the fundamental concepts in [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)], and the tools and processes that are required to start building solutions with [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)].  

> [!TIP] 
> Before you begin these lessons, [learn about the HL7 accelerator and the BizTalk tools available](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md).  
  
 The following descriptions provide a general understanding of each [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] tutorial.  
  
## End-to-End tutorial  
 The [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] End-to-End tutorial provides you with detailed steps to facilitate business processes in a subscriber and publisher scenario. This scenario is a situation in which a publisher, for example, an Admissions Discharge and Transfer system sends a message to specific subscribers.  
  
 The message routes to the [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] Interface Engine, which in turn receives, processes, validates, reformats, and then routes the message to the subscribers. The subscribers in this scenario are a Hospital Information System and a Pharmacy System.  
  
 This scenario uses both File and Minimal Lower Layer Protocol (MLLP) adapter types. The publisher does not need to be aware of the subscribers, and the [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] Interface Engine sends an appropriate acknowledgement to the publisher after processing the message.  
  
## Interrogative tutorial  
 The [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] Interrogative tutorial provides you with detailed steps for implementing a query-response system between sub-systems within an organization. In this scenario, a line-of-business (LOB) application in the Admissions, Discharge, and Transfer system sends a query to the Hospital Information System to obtain patient lab results. After the Hospital Information System receives the query, it sends the requested data back to the system that issued the query.  
  
 This scenario uses MLLP as the transport protocol for all messages, including acknowledgments.  
  
## Message enrichment tutorial  
 The [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] Enrichment tutorial provides you with detailed steps to solve a particular business problem: the message-enrichment scenario. The message-enrichment scenario is a situation in which you have to add to, or enrich, a message that is not HL7-compliant and/or is incomplete. This situation can occur with an application, such as a patient-registration application, or when you are populating a message with XML data from [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)].  
  
 In the message enrichment scenario, you capture the messages with [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)], and provide any missing data, for example, from a patient-records database. You then convert the message and send it to a laboratory, insurance, or any legacy line-of-business (LOB) application using the MLLP adapter.  
  
## Batching tutorial  
 The [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] Batching tutorial provides you with detailed steps to receive and send batched messages. Batching involves receiving and/or sending a group of individual messages (or acknowledgments) as a single composite message.  
  
[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] supports the following three message batching scenarios:  
  
- **Fragmented inbound batch**. In this scenario, [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] receives an HL7 message batch, and then routes the individual messages to the destination system.  
  
- **Batch in/batch out**. [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] receives an HL7 message batch, verifies the individual messages within the batch, and then routes the message batch to the destination system.  
  
- **Create batch (or outbound batching)**. [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] receives individual messages and batches them before routing them to the destination system.  
  
## Tutorial links  
  
-   [End-to-End Tutorial](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md)  
  
-   [Interrogative Tutorial](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md)  
  
-   [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)  
  
-   [Batching Tutorial](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)
  
## See also
  
[Accessibility for People with Disabilities](../../adapters-and-accelerators/accelerator-hl7/accessibility-for-people-with-disabilities5.md)