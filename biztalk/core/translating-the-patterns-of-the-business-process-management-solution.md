---
title: "Translating the Patterns of the Business Process Management Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "artifacts, patterns"
  - "patterns [process management solutions], orchestration boundaries"
  - "patterns [process management solutions], translating patterns to artifacts"
  - "orchestrations, patterns"
  - "orchestrations, boundaries"
ms.assetid: 69f37732-f235-4bbb-bc85-31b4971c95ce
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Translating the Patterns of the Business Process Management Solution
This section describes how the solution translates the pattern diagram into BizTalk Server artifacts.  
  
 ![Business Process Management Solution Patterns](../core/media/bts-cp-business-process-management-patterns.gif "bts_cp_Business_Process_Management_Patterns")  
  
## Connections  
 The connections are the message paths among the solution components. The simplest place to begin is with the service interface. BizTalk Server makes it easy to present an orchestration as a Web service. For information about exposing orchestrations as web services, see [How to Map Orchestrations to Web Services](../core/how-to-map-orchestrations-to-web-services.md).  
  
 Other connections exist between the service and the preprocessing section, between the preprocessing section and the process manager, and between the process manager and the processing stages. Connections also include those between the stages and the backend systems, and between the preprocessing and the history database and the servicing system.  
  
> [!NOTE]
>  Translators correspond to BizTalk maps. Maps are, in turn, parts of pipelines or **Transform** orchestration shapes.  
  
 The decision to make the connection to the process manager synchronous or asynchronous requires some thought. Unlike a credit check, an order in a process such as cable service ordering is unlikely to finish quickly. The logic of managing the process is more complex if the connection to the process manager is asynchronous and requires correlation. This solution uses, in effect, an asynchronous connection to the process manager by publishing messages to the MessageBox.  
  
 The connections between the process manager and the stages represent a similar trade-off between conserving server resources and simplifying logic. The stages have shorter processing times than the process manager. Each stage needs to finish its processing before the processing continues in the next stage. However, because we may want to modify the stages, the process manager can't be tightly coupled to the stages. In the application, the connection can be described as a limited publish-subscribe model. The process manager sends messages to the stages through a single, dedicated port. The stages, in turn, filter to recognize messages specifically for them.  
  
## Determining Orchestration Boundaries  
 The pattern falls into three major areas: preprocessing the messages, managing the business process, and the business process itself. The pre-processing consists of handling the connection to the web service, translating messages to messages for the response, notifying the servicing system, making entries in the history database, and transmitting messages to the process manager. In the application, the preprocessing is handled by a single orchestration. Managing the business process is handled by another orchestration. The business process being managed is broken into appropriate stages. Each stage corresponds to an orchestration to allow for additions and deletions representing changes in the order process. For more information about the design of the order process stages, see "Dividing Business Processes" in [Some Design Principles in the Business Process Management Solution](../core/some-design-principles-in-the-business-process-management-solution.md).  
  
## Translating the Components into Orchestrations  
 The first orchestration, **OrderBroker**, translates the diagram simply and directly. The orchestration is primarily mapping shapes used to construct the notification messages and the order message for the process manager. For a complete list of orchestration shapes, see [Orchestration Shapes](../core/orchestration-shapes.md).  
  
 The logic of the process manager and its satellite assemblies is somewhat complex. For information about the logic of the process manager orchestration, **OrderManager**, see [Process Manager Logic](../core/process-manager-logic.md).  
  
## See Also  
 [Patterns in the Business Process Management Solution](../core/patterns-in-the-business-process-management-solution.md)   
 [Designing with Patterns: the Business Process Management Solution](../core/designing-with-patterns-the-business-process-management-solution.md)   
 [Pattern Catalog for the Business Process Management Solution](../core/pattern-catalog-for-the-business-process-management-solution.md)