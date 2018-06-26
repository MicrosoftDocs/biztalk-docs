---
title: "Dynamic Resolution and Routing Overview | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a9a32491-132b-4b25-ac8c-4a927052f0be
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Dynamic Resolution and Routing Overview
The ESB Resolver classes support run-time resolution of the following:  

- Message delivery endpoints  

- Maps for transformation  

- Endpoint configuration  

- Custom service metadata  

- Server-side itineraries  

  The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] uses resolver connection strings to attempt resolution of maps and endpoints when messages arrive. These connections strings may exist in the itinerary SOAP header of messages when they arrive, or they may be set in a custom pipeline using one of the following pipeline components: ESB Itinerary Selector, ESB Dispatcher, or ESB Dispatcher Disassemble. Resolution occurs later in the processing life cycle using the "just-in-time" (JIT) resolution capabilities of the ESB Resolver and Adapter Provider Framework components.  

  For example, if the dynamic transformation agent receives a message that it must map, but the map name has not yet been determined, it will attempt to use the associated resolver to perform the resolution. If JIT resolution fails, which is classed as an error, the system generates an exception message.  

  The Resolver and Adapter Provider Framework can query the following data stores or resolution mechanisms:  

- Hard-coded maps or endpoints, in which case dynamic resolution does not occur  

- A Business Rules Engine (BRE) policy  

- A custom assembly implementing the **IResolveProvider** interface  

- An XPath query over the message  

- A Universal Description, Discovery, and Integration (UDDI) lookup
