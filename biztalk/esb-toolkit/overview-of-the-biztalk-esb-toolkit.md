---
title: "Overview of the ESB Toolkit in BizTalk Server | Microsoft Docs"
description: Explanation of the ESB Toolkit, and what it does in BizTalk Server
caps.latest.revision: 6
author: "MandiOhlinger"
manager: "anneta"

ms.custom: ""
ms.date: "08/10/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3e190b34-40bc-4f27-9b4f-56e98591e1d4
ms.author: "mandia"
---

# What is the BizTalk ESB Toolkit

## Overview
The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] extends the capabilities of BizTalk Server to support a loosely coupled messaging architecture. Most developers are familiar with code-oriented, procedural, or object-oriented development paradigms. However, when starting to develop BizTalk solutions, developers tend to overlook the message-oriented capabilities of BizTalk Server.  
  
 BizTalk Server includes a powerful publish/subscribe mechanism that works by creating and filling subscriptions. When a new message arrives in the BizTalk Message Box database, a message agent identifies subscribers and sends the message to any endpoints that have subscriptions. Subscriptions can be created in several ways, including binding an orchestration to a receive port, having a correlated receive waiting for a message, or creating a send port with a filter condition that matches a property of the message (such as the type, the receive point, or the value of a routable property).  
  
 By providing this efficient and scalable approach, BizTalk Server enables developers to create a series of discrete sub-processes, define the types of messages that trigger their invocation, and not worry about the sequence. A process initiated by the arrival of a message performs its processing on the message; after it processes the message, it can deliver this or another message to the Message Box database, which, in turn, may activate one or more sub-processes.  
  
 Microsoft provides key building blocks that are required for building comprehensive Service-Oriented Infrastructures, including Windows Server, the .NET Framework, and BizTalk Server. The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] is based on BizTalk Server because it provides the basis for the most common ESB services, including the following:  
  
-   Message routing  
  
-   Message validation  
  
-   Message transformation  
  
-   Extensible adapter framework for connectivity  
  
-   Service orchestration  
  
-   Business rules engine  
  
-   Business activity monitoring  
  
-   Web service and WS-* integration (WCF adapter)  

## Core capabilities  
 The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] extends the functionality of BizTalk Server to provide a range of new capabilities focused on building robust, connected, service-oriented applications. The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] treats BizTalk Server components as individual units of work that can be connected, as desired, to form loosely coupled solutions. The following are some of the core capabilities that the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] provides to enhance the capabilities of BizTalk Server:  
  
- **Policy driven mediation.** The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] does the following:  
  
  - It provides itinerary-based routing that supports lightweight service composition at the time of message publication. This approach allows dynamic discovery of service endpoints and mediation requirements for message routing using a service registry or the business rules policy.  
  
  - It adds support for policy centralization for itinerary-based routing using server-side itineraries that are dynamically resolved and added to the message context after a message is received. Managing itineraries in a central location enables the processing of messages from clients that are completely unaware of how their requests are being routed.  
  
  - It uses an enhanced version of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Resolver and Adapter Provider Framework, which enables dynamic resolution of endpoints and transformation requirements; this effectively decouples the consumer from the services.  
  
- **Connecting systems.** The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] does the following:  
  
  -   It provides pipeline components that normalize XML message namespaces.  
  
  -   It integrates with JMS through the WebSphere MQ adapter for BizTalk Server.  
  
  -   It facilitates message exchange patterns that enable dynamic service aggregation, message routing, message validation, and message transformation.  
  
  -   It supports service endpoint discovery from registry and repository integration using UDDI 3.0.  
  
  -   It supports message routing through line-of-business (LOB) adapters by using the WCF-Custom BizTalk Adapter for BizTalk Server.  
  
- **Management and monitoring.** The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] does the following:  
  
  -   It provides exception management framework and tools.  
  
  -   It facilitates message repair and resubmission using a management portal, shipped as a sample application. This Web application also supports customizable e-mail notifications when a specific error occurs.  
  
  -   It allows BizTalk Server endpoint and registry integration, management, and publication.  
  
  -   It provides a centralized repository of versioned server-side itineraries.  
  
  -   It supports reporting and analytics for BizTalk Server applications.  
  
  -   It includes Business Activity Monitoring components to track itinerary service execution, including start time, end time, and service mediation sequence.  
  
- **SOA governance.** The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] does the following:  
  
  -   It integrates with third-party SOA governance solutions, including embedded management agents for BizTalk Server from AmberPoint and SOA Software.  

> [!TIP]
> [Understanding BizTalk Server](../core/understanding-biztalk-server.md) provides more details on the messaging engine, and more.

## Get some help
Get some help, and help others at the [BizTalk ESB Toolkit forums](http://go.microsoft.com/fwlink/?LinkID=185951&clcid=0x409).

## Next steps
[Contents of the BizTalk ESB Toolkit](contents-of-the-biztalk-esb-toolkit.md)  
