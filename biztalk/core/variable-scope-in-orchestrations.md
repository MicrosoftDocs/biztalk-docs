---
description: "Learn more about: Variable Scope in Orchestrations"
title: "Variable Scope in Orchestrations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, variables"
ms.assetid: 5856cdca-0ebd-4e16-8739-7bd50753b9f9
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Variable Scope in Orchestrations
There are a few important points to understand about the visibility and state of variables and orchestration parameters in various places within your orchestration, including exception handlers and compensation blocks.  
  
-   Orchestration parameters are visible throughout the body of the orchestration as well as in its compensation block.  
  
-   Scope-level variables are visible in the body of the scope as well as in all of its exception handlers and compensation block. Inside exception handlers, the variables are considered un-initialized since it is indeterminate whether the exception that led to a given handler took place before or after any initialization in the body. For this reason, if you declare a variable in a scope and initialize it in the body, you cannot read from it in an exception handler, or you will get a compiler error. A workaround for that exists in the case of long running transactions. The following example shows how the succeeded() operator can be used to ensure proper runtime behavior:  
  
    > [!NOTE]
    >  The code below is pseudo code that describes a logical process; this code cannot be used within an Orchestration Expression shape.  
  
    ```  
    scope longrunning transaction L  
    {  
       System.Int32 i;  
       System.Int32 v;  
       body  
       {  
          i = 3;  
          scope longrunning transaction T  
          {  
             body  
             {  
                i = 5;  
             }  
          }  
       }  
       exceptions  
       {  
          catch  
          {  
             if(succeeded(T))  
             {  
                v = i;  // OK to read from it here — no compiler errors!  
             }  
          }  
       }  
    }  
    ```  
  
-   Inside a compensation block, all variables assume the values they had when the body of the scope committed. Note that the compensation block of a scope never runs immediately after its body completes; there is always intervening code. If any of that intervening code updates some outer-scope variables, and then the compensation block runs, those updates will not be seen inside the compensation block. Instead the variables will temporarily revert to the values they had at the time the scope which owns that compensation had committed.  
  
-   When a transaction is nested inside a loop, the transaction will be compensated as many times as the loop executes. Inside the compensation block for each iteration, outer-scope variables assume the values they had at the time of the iteration of the transaction committed.  
  
-   Any updates made to outer-scope variables or orchestration parameters inside compensation blocks of inner scopes will not be visible after the compensation block completes. In other words, the compensation block cannot be used to directly modify the values of outer-scope variables.  
  
## See Also  
 [XLANG-s Data Types](../core/xlang-s-data-types.md)
