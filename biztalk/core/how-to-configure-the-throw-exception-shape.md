---
description: "Learn more about: How to Configure the Throw Exception Shape"
title: "How to Configure the Throw Exception Shape"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Configure the Throw Exception Shape
You can explicitly throw exceptions in an orchestration by using the **Throw Exception** shape. When the throw is performed, the runtime engine will search for the nearest exception handler that can handle the type of exception being thrown.  
  
 First, the current orchestration is searched for an enclosing scope, and the associated exception handlers of the scope are considered in order to locate the appropriate handler for the type of exception that has been thrown.  
  
 If no appropriate exception handler is found, the orchestration that called the current orchestration is searched for a scope that encloses the point of the call to the current orchestration. This search continues until an exception handler is found that can handle the current exception.  
  
 An exact match for the exception is an exception class that is of the same class as, or a base class of, the run-time type of the exception being thrown.  
  
 After a matching exception handler is found, control is transferred to the first statement of the exception handler.  
  
 If the search for matching exception handlers fails, the orchestration halts. Transactions can help you minimize the impact of such an occurrence.  
  
## Procedure  
  
#### To configure a Throw Exception shape  
  
-   In the Properties window, select an available object type to throw from the **Exception Object** drop-down list.  
  
    > [!NOTE]
    >  Select General Exception in the **Throw Exception** shape only if the **Throw Exception** shape is within an exception handler and you want to rethrow the exception caught in the current exception handler. You will receive an error during the compile if you use General Exception for a **Throw Exception** shape in any other context.  
  
## See Also  
 [Exceptions](../core/exceptions.md)
