---
description: "Learn more about: Decoupling Transport Type and Processing"
title: "Decoupling Transport Type and Processing"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Decoupling Transport Type and Processing
In a service oriented solution, a clear line often exists between the business processing and the specifics of transmitting and receiving messages. This enables you to change the business process or the messaging part of the solution independently.  
  
 The service oriented solution violates this design principle in one place. This section describes the situation, the possible alternatives, and the selected structure.  
  
## Correlation and the MQSeries Adapter  
 In order to use the MQSeries adapter, you cannot use the standard BizTalk Server correlation identifiers. This is because the correlation identifier goes to an IBM back-end system that has its own system of correlation identifiers. Instead, you must use the **MQSeries.MQMD_CorrelId** and **MQSeries.MQMD_MsgID** properties. Using these properties potentially puts transport-specific information in the orchestration and, thus, in the business process.  
  
 One way to handle this dependency would be to use the BizTalk Server correlation identifier and use a custom pipeline component to translate the correlation identifier for MQSeries. This adds complexity to the scenario. In addition, if the transport changes, two pipeline components must be changed. And, ultimately, it relocates the dependency (in the pipeline component) rather than resolving it.  
  
 Another option would be to isolate the MQSeries-specific correlation handling to a separate orchestration and call that orchestration. This would preserve the independence of the business process. However, this introduces a compile-time dependency between the orchestrations. Modifying the transport requires recompiling both orchestrations (as, for example, in going from the stub to the adapter version of the solution). The call also adds to the response time for the solution.  
  
 Given the additional complexity and possible decrease in performance, it seemed simplest to use the MQSeries correlation directly in the orchestration.  
  
 For more information about the adapter and correlations in orchestrations, see [MQSCorrelationSetOrchestration (BizTalk Server Sample)](../core/mqscorrelationsetorchestration-biztalk-server-sample.md).  
  
## See Also  
 [Implementation Highlights of the Service Oriented Solution](../core/implementation-highlights-of-the-service-oriented-solution.md)   
 [MQSCorrelationSetOrchestration (BizTalk Server Sample)](../core/mqscorrelationsetorchestration-biztalk-server-sample.md)
