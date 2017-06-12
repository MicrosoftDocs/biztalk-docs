---
title: "Developing a Service Oriented Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tutorials, developing"
  - "service solution tutorial, background information"
  - "service solution tutorial, developing"
  - "developing, tutorials"
  - "developing, service solution tutorial"
ms.assetid: 7979a05c-7fd3-4476-a623-55de8abdc493
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Developing a Service Oriented Solution
The service oriented solution demonstrates a credit account balance system for Woodgrove Bank. Information about an account comes from three legacy systems: an SAP system that provides the credit limit, a pending transactions system running on a mainframe, and a payment tracking system using MQSeries. Balance check requests come through a Web service or an Interactive Voice Response (IVR) system. For more information about the scenario, see [Understanding the Service Oriented Solution](../core/understanding-the-service-oriented-solution.md).  
  
 This Developer's Guide presents one approach to building a service oriented architecture solution for the Woodgrove Bank scenario. The Guide begins by considering a possible solution in terms of industry-standard patterns. "Patterns in the Service Oriented Solution" begins the translation of that pattern into the appropriate artifacts of a BizTalk application. The next section, "Components of the Service Oriented Solution," summarizes the various parts of the application and their relationships. The Implementation Highlights section discusses areas—such as using Enterprise Single Sign-On—that required special work to meet the criteria of the scenario. "Monitoring the Service Oriented Solution with BAM" describes how the solution uses the BAM API to track progress of requests and results. The "Versioning the Service Oriented Solution" and "Scaling the Service Oriented Solution" sections suggest ways of extending or modifying the solution. The reference section lists the files in the solution and provides a reference to the messages.  
  
## In This Section  
  
-   [Patterns in the Service Oriented Solution](../core/patterns-in-the-service-oriented-solution.md)  
  
-   [Components of the Service Oriented Solution](../core/components-of-the-service-oriented-solution.md)  
  
-   [Implementation Highlights of the Service Oriented Solution](../core/implementation-highlights-of-the-service-oriented-solution.md)  
  
-   [Monitoring the Service Oriented Solution with BAM](../core/monitoring-the-service-oriented-solution-with-bam.md)  
  
-   [Versioning the Service Oriented Solution](../core/versioning-the-service-oriented-solution.md)  
  
-   [Scaling the Service Oriented Solution](../core/scaling-the-service-oriented-solution.md)  
  
-   [Service Oriented Solution Reference](../core/service-oriented-solution-reference.md)