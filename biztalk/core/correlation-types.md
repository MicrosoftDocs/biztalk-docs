---
description: "Learn more about: Correlation Types"
title: "Correlation Types | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "correlation sets, correlation types"
  - "correlation types, correlation sets"
  - "correlation types"
  - "validating, correlation types"
  - "correlation types, about correlation types"
  - "correlation types, validating"
ms.assetid: 1aa5ca5c-c37d-4091-9f5d-331a6b202d4e
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Correlation Types
Each correlation set is based on a **correlation type**, which is simply a list of properties. These properties might be data properties, which are found in the message itself, or context properties, which describe details of the system or messages that are unrelated to the data being conveyed in the message.  
  
 You can use a correlation type in more than one correlation set. If you need to correlate on different values for the properties in a correlation type, you must create a new correlation set—each correlation set can be initialized only once.  
  
 You can promote properties in a property schema to declare that certain properties in a message are accessible to your orchestration. For more information, see [Promoting Properties](../core/promoting-properties.md).  
  
> [!CAUTION]
>  Do not set the system-defined property **BTS.CorrelationToken** that is associated with each message. This is used by the engine in correlating messages, and setting it could result in your orchestration losing messages.  
  
## Validating Message Correlation on Send Actions  
 You can validate the properties of a message that you send from your orchestration to ensure that it reflects the properties in its correlation set. By default, this validation is disabled. For information on how to enable it, see [Runtime Validation for the Orchestration Engine](../core/runtime-validation-for-the-orchestration-engine.md).
