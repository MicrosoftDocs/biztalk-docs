---
description: "Learn more about: Service Management Patterns"
title: "Service Management Patterns"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Service Management Patterns
## Repair and Resubmit  
 The Repair and Resubmit pattern defines a solution in which a service is unable to process a message and needs to gracefully externalize its state in the form of the failed message, enabling the message content to be available for repair and then resubmit it to a service to continue processing the message.  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes mechanisms by which Microsoft BizTalk messaging and orchestration exceptions can be normalized and exposed for additional action. When designing an ESB solution, it is important to account for how exceptions will be handled. The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes a sample ESB Management Portal application that demonstrates how exceptions can be viewed and managed. For detailed information about repairing and resubmitting exceptions using the ESB Management Portal sample application, see [Repairing and Resubmitting Messages](../esb-toolkit/repairing-and-resubmitting-messages.md).
