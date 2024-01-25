---
description: "Learn more about: Correlation Types"
title: "Correlation Types"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Correlation Types
Each correlation set is based on a **correlation type**, which is simply a list of properties. These properties might be data properties, which are found in the message itself, or context properties, which describe details of the system or messages that are unrelated to the data being conveyed in the message.  
  
 You can use a correlation type in more than one correlation set. If you need to correlate on different values for the properties in a correlation type, you must create a new correlation set—each correlation set can be initialized only once.  
  
 You can promote properties in a property schema to declare that certain properties in a message are accessible to your orchestration. For more information, see [Promoting Properties](../core/promoting-properties.md).  
  
> [!CAUTION]
>  Do not set the system-defined property **BTS.CorrelationToken** that is associated with each message. This is used by the engine in correlating messages, and setting it could result in your orchestration losing messages.  
  
## Validating Message Correlation on Send Actions  
 You can validate the properties of a message that you send from your orchestration to ensure that it reflects the properties in its correlation set. By default, this validation is disabled. For information on how to enable it, see [Runtime Validation for the Orchestration Engine](../core/runtime-validation-for-the-orchestration-engine.md).
