---
description: "Learn more about: Transacted Orchestrations"
title: "Transacted Orchestrations"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Transacted Orchestrations
Orchestrations can be transactional, just like scopes. In fact, an orchestration can itself be considered a scope. In general, the same rules apply for transacted orchestrations as for transacted scopes.  
  
> [!NOTE]
>  One difference between orchestrations and other scopes is that orchestrations do not have exception handlers.  
  
## Orchestration compensation  
 If the **Transaction Type** property for your orchestration is set to long-running or atomic, you can also select a value for the **Compensation** property, which can be Default or Custom.  
  
 If you select **Custom** for the compensation, a **Compensation** tab will appear alongside the Orchestration Design Surface. It will look the same as the Orchestration Design Surface, and you can add shapes and ports to it in the same way.  
  
 Compensations only take place on orchestrations that are called by other orchestrations. You can compensate a specific orchestration instance by using the **Identifier** property on the **Call Orchestration** shape.  
  
> [!IMPORTANT]
>  If a compensation exists on a top-level orchestration, it will be ignored by the runtime engine.  
  
## See Also  
 [Making Orchestrations Transactional](../core/making-orchestrations-transactional.md)   
 [Using Transactions and Handling Exceptions](../core/using-transactions-and-handling-exceptions.md)
