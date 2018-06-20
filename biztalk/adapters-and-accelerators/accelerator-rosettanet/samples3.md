---
title: "Samples3 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SDK samples"
  - "examples, developing"
  - "developing, examples"
ms.assetid: b940111e-4f71-494b-b7a3-d2e8310bea51
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Samples
This section describes the samples included in the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Software Development Kit (SDK). This section provides detailed information about each sample, including how to build the sample, how to run it, and what results to expect.  

 The samples are included in the \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\ folder.  

## In This Section  

- Adapter samples folder  

  -   [ApplicationAdapter](../../adapters-and-accelerators/accelerator-rosettanet/applicationadapter.md). Demonstrates how to include a message notification mechanism.  

  -   [ValidationAdapter](../../adapters-and-accelerators/accelerator-rosettanet/validationadapter.md). Demonstrates how to run special validation rules on a message.  

- Messaging samples folder  

  -   [FileTransport Sample](../../adapters-and-accelerators/accelerator-rosettanet/filetransport-sample.md). Demonstrates how to configure BTARN to use File ports.  

  -   [GetMessages Sample](../../adapters-and-accelerators/accelerator-rosettanet/getmessages-sample.md). Demonstrates how to retrieve messages from either of the non-repudiation tables or one of the line-of-business (LOB) tables.  

  -   [Message Submission ASPX Sample](../../adapters-and-accelerators/accelerator-rosettanet/message-submission-aspx-sample.md). Provides sample .aspx code for submitting service content to a private process. Also provides HTML for submitting a Partner Interface Process (PIP) action message to that service content.  

  -   [Tracking Sample](../../adapters-and-accelerators/accelerator-rosettanet/tracking-sample.md). Provides sample .aspx code for viewing the status of messages sent and received with BTARN.  

- Orchestration samples folder  

  -   [3A4 Private Responder Orchestration Using a Business Rule](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md). Demonstrates how to automate a business process involving PIPs using a map transforming a request message to a response message.  

  -   [Double Action PIPAutomation Orchestration](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md). Demonstrates how to automate a business process, with automatic determination of the response message type based on the incoming message type.  

  -   [3A2 Request to 3A2 Response Map Sample](../../adapters-and-accelerators/accelerator-rosettanet/3a2-request-to-3a2-response-map-sample.md). Demonstrates how to map a 3A2 Request schema to a 3A2 Response schema.  

  -   [3A4 Request to 3A4 Response Map Sample](../../adapters-and-accelerators/accelerator-rosettanet/3a4-request-to-3a4-response-map-sample.md). Demonstrates how to map a 3A4 Request schema to a 3A4 Response schema.  

  -   [PrivateInitiator Sample](../../adapters-and-accelerators/accelerator-rosettanet/privateinitiator-sample.md). Demonstrates how to create an initiator private-process orchestration.  

  -   [PrivateResponder Sample](../../adapters-and-accelerators/accelerator-rosettanet/privateresponder-sample.md). Demonstrates how to create a responder private-process orchestration.  

  -   [HubScenario Sample](../../adapters-and-accelerators/accelerator-rosettanet/hubscenario-sample.md). Demonstrates how to transform a message sent to an intermediary hub, into a message to be sent to the final recipient.  

- Pipeline samples folder  

  - [Send Pipeline](../../adapters-and-accelerators/accelerator-rosettanet/send-pipeline.md). Demonstrates how to process outgoing XML messages into the equivalent RNIF messages by using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pipelines.  

  - [Receive Pipeline](../../adapters-and-accelerators/accelerator-rosettanet/receive-pipeline.md). Demonstrates how to process incoming RNIF messages into the equivalent XML messages by using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pipelines.  

  - [Message Editor Pipeline Sample](../../adapters-and-accelerators/accelerator-rosettanet/message-editor-pipeline-sample.md). Demonstrates how to create a custom pipeline component to edit incoming messages.  

- Schema samples folder  

  -   [Schema Samples](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md). Describes the sample schemas provided in the SDK, including PIP XML schemas, RosettaNet next-generation schemas, and RNIF schemas. Includes pointers to procedures for using these schemas.  

- Web Application sample folder  

  -   [RNIFSend](../../adapters-and-accelerators/accelerator-rosettanet/rnifsend.md). Demonstrates how to customize the ASPX page that sends RNIF messages from the initiator to the responder.  

  -   [RNIFReceive](../../adapters-and-accelerators/accelerator-rosettanet/rnifreceive.md). Demonstrates how to customize the ASPX page that receives RNIF messages at the responder.  

- [Stopping and Starting Orchestrations, Send Ports, and Receive Locations Programmatically](../../adapters-and-accelerators/accelerator-rosettanet/code-to-stop-and-start-orchestrations-send-ports-and-receive-locations.md). Demonstrates how to stop and start all orchestrations, send ports, and receive locations as a group or individually.
