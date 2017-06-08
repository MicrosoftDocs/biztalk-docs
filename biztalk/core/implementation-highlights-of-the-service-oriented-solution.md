---
title: "Implementation Highlights of the Service Oriented Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "service solution tutorial, performance"
  - "performance, service solutions"
  - "service solution tutorial, implementing"
ms.assetid: 3dbd8dfd-45b7-4290-ba07-b0c5e6264629
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Implementation Highlights of the Service Oriented Solution
A solution solves a particular problem in a specific context. The Service Oriented solution is no exception and is specific to Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the scenario. For more information about the Woodgrove Bank scenario, see [Understanding the Service Oriented Solution](../core/understanding-the-service-oriented-solution.md).  
  
 While developing the scenario, several areas proved to be bottlenecks in reducing response times to an acceptable level. Sending messages to the backend systems using the adapters introduces significant latency in getting back responses. In general, adapters by themselves offer very low latency. However, the distributed architecture of BizTalk requires adapters to communicate with the orchestration host instances using the message box. This introduces round trips to the database and affects latency times. For this reason, the inline version of the solution (the fastest version) builds the adapter functionality in the orchestration itself calls the back-end systems directly. With three different back-end systems, that means potentially three different mechanisms to communicate with the back-end systems.  
  
 Another area that proved a performance problem was retrieving configuration data from Enterprise Single Sign-On (SSO). To retain the convenience and universality of SSO while speeding up retrieval time, the solution uses a local cache for configuration values. Using SSO also allows easier management of the configuration data. Adding additional host instances to meet latency and performance requirements does not require changing settings on the server running the host instance.  
  
 Another unusual element of the solution is calling pipelines directly from code. This allows reuse of the custom pipeline components.  
  
 Finally, there are several BizTalk Server settings that you can change to squeeze out the last bit of speed from the solution.  
  
## In This Section  
  
-   [Inlining Back-end Invocation](../core/inlining-back-end-invocation.md)  
  
-   [Using SSO Efficiently in the Service Oriented Solution](../core/using-sso-efficiently-in-the-service-oriented-solution.md)  
  
-   [Using Pipelines from the Service Oriented Solution](../core/using-pipelines-from-the-service-oriented-solution.md)  
  
-   [Tuning the Service Oriented Solution](../core/tuning-the-service-oriented-solution.md)  
  
-   [Decoupling Transport Type and Processing](../core/decoupling-transport-type-and-processing.md)