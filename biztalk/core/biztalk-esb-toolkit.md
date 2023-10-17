---
description: "Learn more about: BizTalk ESB Toolkit"
title: "BizTalk ESB Toolkit | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 08035518-17ad-44d2-ab06-90d725c95ced
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk ESB Toolkit
The Microsoft BizTalk ESB Toolkit uses Microsoft BizTalk Server to support a loosely coupled messaging architecture. BizTalk Server includes a powerful publish/subscribe mechanism for messaging applications that works by creating and filling subscriptions, which provides a highly efficient and scalable platform for service-oriented architecture (SOA) applications. The BizTalk ESB Toolkit extends the functionality of BizTalk Server to provide a range of new capabilities focused on building robust, connected, service-oriented applications that incorporate itinerary-based service invocation for lightweight service composition, dynamic resolution of endpoints and maps, Web service and WS-* integration, fault management and reporting, and integration with third-party SOA governance solutions.

## Overview
 The BizTalk ESB Toolkit provides architectural guidance, patterns, and a collection of BizTalk Server and .NET Framework components to simplify the development of an Enterprise Service Bus (ESB) on the Microsoft platform and to allow Microsoft customers to extend their own messaging and integration solutions.

## Common Scenarios
 The term Enterprise Service Bus (ESB) is widely used in the context of implementing an infrastructure for enabling a service-oriented architecture (SOA). However, real-world experience with the deployment of SOAs has shown that an ESB is only one of many building blocks that make up a comprehensive Service-Oriented Infrastructure (SOI). The term ESB has morphed in a number of different directions, and its definition depends on the interpretation of individual ESB and integration platform vendors and on the requirements of particular SOA initiatives. Based on the experience Microsoft has gathered from many successful real-world SOI implementations, you can think of an ESB as a collection of architectural patterns based on traditional enterprise application integration (EAI), message-oriented middleware, Web services, .NET and Java interoperability, host system integration, and interoperability with service registries and asset repositories.

## Audience Requirements
 The BizTalk ESB Toolkit is intended for developers who create Microsoft BizTalk Server solutions or other solutions that use the BizTalk ESB Toolkit components. To take full advantage of the BizTalk ESB Toolkit, developers should possess knowledge and experience working with the following:

1.  Microsoft BizTalk Server

2.  Microsoft Visual Studio

3.  Microsoft .NET development techniques, including the development of ASP.NET Web services and .NET Framework components

## How the BizTalk ESB Toolkit Works
 The BizTalk ESB Toolkit accepts inbound messages and operates on them, perhaps (but not always) by performing processes such as transformation, delivery, or any other custom defined process. To specify the operations required, the core processing components require a message to contain associated instructions or metadata that define the processes to apply and the tasks to execute with the message content.
This approach provides loose coupling between services; this means that the ESB does not require prior knowledge of the specific processing for each message. It just has to know the possible range of processes and how to apply each process. The wide range of options for specifying the available processes and the mapping between the processes and the instructions within messages provides a flexible mechanism for configuring and adjusting behavior, without requiring changes to code and redeployment of components.

## Getting Started
 After installing the BizTalk ESB Toolkit, you should read the "Getting Started" topic in the [BizTalk ESB Toolkit Documentation](https://go.microsoft.com/fwlink/?LinkId=193578) to understand the architecture, message flow, and the core components of the BizTalk ESB Toolkit. You should also install and run the samples included with the BizTalk ESB Toolkit, which demonstrate the common use cases described in the "Getting Started" topic and other messaging scenarios. This approach will help you quickly grasp how the BizTalk ESB Toolkit works and how you can take advantage of its features in your own SOA applications.

## See Also
 [BizTalk Enterprise Service Guidance](https://go.microsoft.com/fwlink/?LinkId=193577)
 [Service Oriented Solution](../core/service-oriented-solution.md)
 [Using Web Services](../core/using-web-services.md)
