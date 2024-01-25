---
description: "Learn more about: Error Handling"
title: "Error Handling"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Error Handling
The pathway that a message follows through the BizTalk Server messaging subsystem encompasses several points of processing and transfer. At each point along this pathway, failures can occur in both BizTalk Server infrastructure and application-provided elements such as custom pipeline components and orchestrations.  
  
 This section and those contained within discuss the typical failure modes of well-known stages of processing and how those failure modes are addressed through both BizTalk Server configuration and application-provided elements such as orchestrations. Failure effects include disposition of the message, diagnostics captured and logged, and operational considerations.  
  
 The events that occur when a message fails are dependent upon the location of the failure and the status of failed message routing and recoverable interchange processing. The table below summarizes the failure behavior and resume location for pipeline and subscription failures.  
  
|Failure Type|Failed message routing|Recoverable Interchange Processing|Failure Behavior|Resume Location|  
|------------------|----------------------------|----------------------------------------|----------------------|---------------------|  
|Pipeline|Disabled|Disabled|Message is suspended before pipeline|Before pipeline.|  
|Pipeline|Disabled|Enabled|Message is suspended after pipeline|Before pipeline. For more information about Recoverable Interchange Processing, see [Recoverable Interchange Processing](../core/recoverable-interchange-processing.md).|  
|Pipeline|Enabled|Disabled|Message is published with error-report-related message context properties promoted|Message is not suspended. For details about routing failed messages, see [Using Failed Message Routing](../core/using-failed-message-routing.md).|  
|Pipeline|Enabled|Enabled|Message is published with error-report-related message context properties promoted.|Message is not suspended.|  
|Subscription|Disabled|Disabled|Message is suspended before pipeline. Routing failure report created.|Message will resume before pipeline. The routing failure report is non-resumable.|  
|Subscription|Disabled|Enabled|Message is suspended after pipeline. Routing failure report created.|Message will resume before pipeline. The routing failure report is non-resumable. For more information about Recoverable Interchange Processing, see [Recoverable Interchange Processing](../core/recoverable-interchange-processing.md).|  
|Subscription|Enabled|Disabled|Message is published with error-report-related message context properties promoted. Routing failure report created.|Message is not suspended. The routing failure report is non-resumable. For details about routing failed messages, see [Using Failed Message Routing](../core/using-failed-message-routing.md).|  
|Subscription|Enabled|Enabled|Message is published with error-report-related message context properties promoted. Routing failure report created.|Message is not suspended. The routing failure report is non-resumable.|  
  
 Many of these enumerated failure modes correspond to specific features of BizTalk Server that are designed to address the failure mode, such as recoverable interchange processing and error reporting. Other failure modes concern how BizTalk Server communicates failure information to application elements and, in turn, how application elements such as custom pipeline components, adapters, and orchestrations communicate failure information to BizTalk Server.  
  
## In This Section  
  
-   [Using Failed Message Routing](../core/using-failed-message-routing.md)  
  
-   [How to Enable Routing for Failed Messages](../core/how-to-enable-routing-for-failed-messages.md)  
  
-   [Using Acknowledgments](../core/using-acknowledgments.md)  
  
## See Also  
 [Recoverable Interchange Processing](../core/recoverable-interchange-processing.md)   
 [Types of Message Failures](../core/types-of-message-failures.md)
