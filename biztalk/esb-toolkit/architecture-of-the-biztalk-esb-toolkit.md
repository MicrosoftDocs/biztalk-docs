---
title: "Architecture of the BizTalk ESB Toolkit | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a41674f5-5ea4-4a8f-a270-b67fd6854028
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Architecture of the BizTalk ESB Toolkit
The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] consists of a series of interoperating components that support and implement a loosely coupled messaging environment that makes it easier to build message-based enterprise applications. The services and components fall naturally into the following seven categories:  
  
- **Web services.** These expose internal services such as itinerary processing, exception management, resolution of endpoints and maps, BizTalk Server operations, Universal Description, Discovery, and Integration (UDDI) interoperation, and transformation of message content.  
  
- **Itinerary services.** These include orchestration-based and messaging-based services for performing transformations and message routing. You can create custom services that participate in Itinerary processing. These include orchestration-based and messaging-based services for performing transformations and message routing. You can create custom services that participate in Itinerary processing.  
  
- **Itinerary on-ramps.** These receive external messages, attach the appropriate itinerary for each message, and perform itinerary processing; they use the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Resolver and Adapter Provider Framework for dynamic resolution of endpoints and metadata.  
  
- **On-ramps.** Unlike itinerary on-ramps, these receive external messages in a range of formats and transports, such as HTTP, Java Message Service (JMS), IBM WebSphere MQ (WMQ), File Transfer Protocol (FTP), Flat File, and XML. They are typical BizTalk Server receive locations that optionally use the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] interop pipeline components and the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Resolver and Adapter Provider Framework for dynamic resolution of endpoints and metadata.  
  
- **Off-ramps.** These implement send ports for the delivery of messages using formats and transports such as WCF, JMS, WMQ, FTP, HTTP, Flat File, XML, or any other custom formats. They are typical BizTalk Server dynamic send ports that are direct-bound to the Message Box and optionally use the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] interop pipeline components and the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Resolver and Adapter Provider Framework for dynamic resolution of endpoints and metadata.  
  
- **Exception Management Framework.** This includes the exception Web service, the exception management API, and components that enrich, process, and pass exception details to the ESB Management Portal.  
  
- **ESB Management Portal.** This sample application provides registry provisioning, exception mediation, alert notification, and analytics.  
  
  Many of these components and services rely on features implemented by BizTalk Server, such as the Orchestration, Transformation, and Business Rules engines and the Message Box database. Figure 1 shows a schematic view of the categories, the components and services typically occurring within each category, and the core BizTalk Server system components used by the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].  
  
  ![ESB Architecture](../esb-toolkit/media/esbarchitecture.gif "ESBArchitecture")  
  
  **Figure 1**  
  
  **The architecture and components of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]**  
  
## How the BizTalk ESB Toolkit Works  
 The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] accepts inbound messages and operates on them, perhaps (but not always) by performing processes such as transformation, routing, or any other custom defined process. To specify the operations required, the core processing components require each message to have a routing slip that contains associated instructions or metadata that define the processes to apply and the tasks to execute with the message content. These routing slips are referred to as itineraries and can be automatically resolved, retrieved from a central repository, and attached to a message when it is received by an on-ramp.  
  
 This routing slip approach provides loose coupling between services, meaning that the ESB does not require prior knowledge of the specific processing for each message. It just has to know what the possible range of processes is and how to apply each process. The wide range of options for specifying the available processes and the mapping between the processes and the instructions within messages provides a flexible mechanism for configuring and adjusting behavior, without requiring changes to code and redeployment of components.  
  
## Design Patterns  
 The architecture that ESB uses, where processes deposit messages in the Message Box database and subscribers pick them up based on a processing instruction in the message, effectively implements the state-machine design pattern. In addition, the ESB implements and exposes its core functionality in a services-oriented manner, including to external applications through a set of core Web services.  
  
 This loosely coupled approach to designing BizTalk Server and [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]-based applications yields highly flexible solutions and has become an industry-accepted best practice.