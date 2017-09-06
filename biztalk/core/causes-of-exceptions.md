---
title: "Causes of Exceptions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, errors"
  - "errors, orchestrations"
  - "errors, causes"
ms.assetid: b0422382-d034-4c58-87c6-fc269dbbfe43
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Causes of Exceptions
Exceptions can be generated within an orchestration in the following ways:  
  
-   By a **Throw Exception** shape, which throws an exception immediately and unconditionally. Control passes from the **Throw Exception** shape directly to the appropriate exception handler.  
  
-   By a time-out expiring in a long-running transaction. A predefined system exception—**Microsoft.XLANG.BaseTypes.TimeOutException**—is thrown in this case.  
  
-   By some other transaction failure. The runtime engine throws a system-defined message such as Microsoft.XLANG.BaseTypes.PersistenceException for these failures.  
  
-   By a user code exception. When calls to external user code are made within an orchestration, common language runtime classes that are called can throw exceptions. If these exceptions are not handled in the user code, they eventually propagate up into the scope in which the call to the user code is made.  
  
-   By some other system exception (for example, a persistence failure, another .NET or system exception such as type loader exception, or a data conversion error).  
  
> [!NOTE]
>  When a type loader exception is thrown, the exception may not be caught in the **Catch Exception** block in the same **Scope** shape. This is because of that the exception is from the type loader, not from the BizTalk orchestration process. Therefore, it does not follow the BizTalk rules of control flow.  
  
-   By a sibling branch in a surrounding scope halting execution. Microsoft.XLANG.BaseTypes.ForcedTerminationException is thrown to each branch in this case, and you might want to add an exception handler to each. Such an exception handler cannot re-throw its exception, nor should it attempt to throw any other type of exception.  
  
-   By receipt of an external message that indicates a fault.  
  
## See Also  
 [Fault Messages](../core/fault-messages.md)   
 [Exceptions](../core/exceptions.md)