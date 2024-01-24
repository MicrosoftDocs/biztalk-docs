---
description: "Learn more about: Inlining Back-end Invocation"
title: "Inlining Back-end Invocation"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Inlining Back-end Invocation
The inline call version, of the full solutions, provides the fastest processing times. The inline version eliminates the overhead of persisting the request and response messages to and from the backend systems in the MessageBox database. In the adapter version, the message goes from the sending orchestration to the MessageBox. The host running the adapter picks up the message, and sends the message to the back-end process by again posting it to the message box.  
  
 The efficiency of inlining comes at a cost of binding the orchestration directly to the transport protocols of the back-end systems. In the inline version, rather than communicating through logical ports, the orchestration calls the back-end systems through three custom assemblies. If a back-end system transport changes, an assembly must be rewritten and recompiled. The following table describes the assemblies and their function:  
  
|Assembly Name|Back-end Connection|  
|-------------------|--------------------------|  
|Microsoft.Samples.BizTalk.WoodgroveBank.PaymentTrackerCall|Uses MQSeries **get** and **put** message functions.|  
|Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactionsCall|Invokes the Web service for the transaction system.|  
|Microsoft.Samples.BizTalk.WoodgroveBank.SAPCall|Calls the web services simulating SAP.|  
  
## See Also  
 [Implementation Highlights of the Service Oriented Solution](../core/implementation-highlights-of-the-service-oriented-solution.md)   
 [Developing a Service Oriented Solution](../core/developing-a-service-oriented-solution.md)   
 [Translating the Patterns of the Service Oriented Solution](../core/translating-the-patterns-of-the-service-oriented-solution.md)   
 [Monitoring the Service Oriented Solution with BAM](../core/monitoring-the-service-oriented-solution-with-bam.md)
