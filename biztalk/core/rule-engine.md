---
title: "Rule Engine | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RuleEngine object"
  - "Business Rules Engine, ruleset executor"
  - "Business Rules Engine, ruleset translator"
  - "Business Rules Engine, ruleset tracking interceptor"
  - "Business Rules Engine, Business Rules Engine"
ms.assetid: c4043a1f-357f-47bc-84e1-5e4bd9f8b5b8
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Rule Engine
This section describes several components, functionalities, and operations of the Business Rule engine. The rule engine provides the execution context for a rule set. The **RuleEngine** object uses the following plug–in components for implementation:  
  
-   **Ruleset executor (inference engine)**. Implements the algorithm responsible for rule condition evaluation and action execution. The default rule set executor is a discrimination network-based forward-chaining inference engine designed to optimize in-memory operation.  
  
-   **Ruleset translator**. Takes as input a **RuleSet** object and produces an executable representation of the rule set. The default in-memory translator creates a compiled discrimination network from the rule set definition.  
  
-   **Rule set tracking interceptor**. Receives output from the rule set executor (inference engine) and forwards it to rule set tracking and monitoring tools.  
  
## In This Section  
  
-   [Condition Evaluation and Action Execution](../core/condition-evaluation-and-action-execution.md)  
  
-   [Agenda and Priority](../core/agenda-and-priority.md)  
  
-   [Engine Control Functions](../core/engine-control-functions.md)  
  
-   [Data Access in the Business Rule Engine](../core/data-access-in-the-business-rule-engine.md)  
  
-   [Rule Action Side Effects](../core/rule-action-side-effects.md)  
  
-   [Support for Class Inheritance in the Business Rule Engine](../core/support-for-class-inheritance-in-the-business-rule-engine.md)  
  
-   [Rule Engine Configuration and Tuning Parameters](../core/rule-engine-configuration-and-tuning-parameters.md)  
  
-   [Performance Considerations When Using the Rule Engine](../core/performance-considerations-when-using-the-rule-engine.md)  
  
## See Also  
 [Business Rules Engine](../core/business-rules-engine.md)