---
title: "Using Itinerary-Based Routing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d5b5d13-cbf2-4f3c-8a1a-3bb852f048a0
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Itinerary-Based Routing
The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] provides itinerary-based message routing by implementing the Routing Slip pattern to enable scenarios when the sequence of processing steps for a particular message is not known at design time and may vary for each message. The implementation of this pattern uses a routing slip to represent a collection of these steps in XML format and determines which steps need to occur during at run time. A state of the routing slip, frequently referred to as an "ESB itinerary," is an ordered set of declarative instructions that define the steps that must be executed for a message as it is being processed by [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] components and the BizTalk Server runtime. A particular processing instruction specified in ESB itinerary is associated with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] component, which is also referred to as the "ESB itinerary service." The purpose of the ESB itinerary service is to execute the processing instructions and to update the state of the routing slip to indicate the next pending instruction.  

 This section describes the itinerary-based processing features of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]. It contains the following topics:  

- [ESB Itinerary Management](../esb-toolkit/esb-itinerary-management.md)  

- [On-Ramps and Off-Ramps](../esb-toolkit/on-ramps-and-off-ramps.md)  

- [Choosing Between Messaging and Orchestration Itinerary Services](../esb-toolkit/choosing-between-messaging-and-orchestration-itinerary-services.md)  

- [Using a Pipeline Component to Select an Existing Itinerary](../esb-toolkit/using-a-pipeline-component-to-select-an-existing-itinerary.md)  

- [Using a Pipeline Component to Read an Itinerary](../esb-toolkit/using-a-pipeline-component-to-read-an-itinerary.md)  

- [Using a Pipeline Component to Cache an Itinerary for Solicit-Response](../esb-toolkit/using-a-pipeline-component-to-cache-an-itinerary-for-solicit-response.md)  

- [Creating Itinerary Subscribers](../esb-toolkit/creating-itinerary-subscribers.md)  

- [Executing an Itinerary Service](../esb-toolkit/executing-an-itinerary-service.md)  

- HYPERLINK "<http://msdn.microsoft.com/library/ee236752(BTS.10).aspx>" [Itinerary-Based Routing Artifacts](../esb-toolkit/itinerary-based-routing-artifacts.md)
