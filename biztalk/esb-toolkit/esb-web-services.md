---
title: "ESB Web Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c122ecdd-344a-4f76-9c73-bf692d479c09
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ESB Web Services
The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contains the following Web services:  
  
- <strong>Itinerary On-ramp Web services.</strong>These services accept external messages and submit the messages for processing. The content of an itinerary contains metadata and processing instructions that describe which services to execute. Routing services define the endpoints to which the message should be routed, while transformation services specify how messages should be transformed. These services support both one-way and two-way (request-response) processing; both ASMX and Windows Communication Foundation (WCF) implementations are provided. The Itinerary On-ramp Web services are not message type–specific, so they accept any message type.  
  
- <strong>Resolver Web service.</strong>This service allows external applications to call the Microsoft ESB Resolver Framework to look up ESB endpoints based on resolution mechanisms supported by the Resolver Framework. The service also offers both ASMX and WCF implementations.  
  
- <strong>Transformation Web service.</strong>This service allows execution of Microsoft BizTalk Server maps without the overhead of Message Box persistence, extending the capability of BizTalk Server map execution to applications that are not based on BizTalk Server. The service offers both ASMX and WCF implementations.  
  
- <strong>Exception Handling Web service.</strong>This service accepts exception messages from external sources and routes using the fault processor pipeline will normalize, track, and publish the exception message to the ESB Management Portal. The service offers both ASMX and WCF implementations.  
  
- <strong>UDDI Web service.</strong>This service enables applications and users to look up endpoints based on the service name, business provider, or business category; it also allows applications and users to manipulate the business providers, services, and categories stored in a UDDI repository. This is a key infrastructure service used by the ESB Management Portal and third-party providers.  
  
- <strong>BizTalk Operations Web service.</strong>This ASMX-based service exposes information about BizTalk Server hosts, orchestration, applications, and status, enabling users and third parties to easily query for application and host status, regardless of the location of computer(s) within the BizTalk Server group. Queries can include message status and flow, status changes, current service instances, and message details. The service can also update receive locations. This is a key infrastructure service used by the ESB Management Portal and third-party providers.  
  
  For more information about the Web services provided as part of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], see [Using the BizTalk ESB Toolkit Web Services](../esb-toolkit/using-the-biztalk-esb-toolkit-web-services.md).