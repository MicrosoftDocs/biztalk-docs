---
title: "Custom Exceptions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "process management solution tutorial, compensation blocks"
  - "compensation blocks, process management solutions"
  - "process management solution tutorial, custom exceptions"
  - "Terminate shape [Orchestration Designer], called orchestrations"
  - "process management solution tutorial, errors"
ms.assetid: 0c923303-82ad-4a20-9c7c-5e38c477993a
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Custom Exceptions
For situations where there is an unrecoverable error, the Business Process Management solution uses a combination of exception handlers and custom exceptions.  
  
## Handling Exceptions  
 Rather than using **Terminate** shapes in called orchestrations you can use the pattern of throwing exceptions that are handled by the root orchestration. This allows the orchestration with the widest knowledge of context to make the decision about handling the exception. Having the subordinate orchestrations throw custom exceptions enables you to communicate more specific information to the root orchestration.  
  
 The business process management solution follows this pattern. There are four root, or uncalled, orchestrations in the solution: **OrderBroker**, **OrderManager**, **CableOrder1**, and **CableOrder2**. Three of the root orchestrations receive and handle custom exceptions: **OrderManager**, **CableOrder1**, and **CableOrder2**.  
  
 Note that some of the root orchestrations use the **Terminate** shape and that the **Terminate** shape appears just before the normal end point of the orchestration. The orchestration still uses the **Terminate** shape in case of an error so that the orchestration is recorded as terminated, rather than as completed but with an error message. This allows the solution to track failed instances easily in addition to recording the error.  
  
 For more information about the **Terminate** shape, see [How to Configure the Terminate Shape](../core/how-to-configure-the-terminate-shape.md). For more information about the **ThrowException** shape, see [How to Configure the Throw Exception Shape](../core/how-to-configure-the-throw-exception-shape.md).  
  
## The Custom Exceptions  
 Each of the following three custom exceptions follows the same pattern. Having distinct types allows the code to distinguish different exceptions.  
  
|Exception|Thrown By (Orchestration)|  
|---------------|---------------------------------|  
|**ActivateException**|**Change**|  
|**CableOrderException**|**Activate**, **CableOrder1**|  
|**InterruptException**|**CableOrder1**, **CheckInterrupt**, **ErrorHandlerOrch**|  
  
 All of the custom exceptions are defined in the **Utilities** assembly. The custom exceptions are all .NET classes. All of the custom exception classes inherit from the .NET **ApplicationException** class which in turn inherits from the **System.Exception** class. Because there is a possibility that the exception may be dehydrated (serialized and stored in the database), the exceptions must implement a deserialization constructor. A deserialization constructor is a constructor that takes two arguments: a SerializationInfo object, and a StreamingContext object. The deserialization constructor will be used during rehydration of the exception. Because the **ApplicationException** class already implements a deserialization constructor, the constructor for the custom exception simply invokes the base (ApplicationException) deserialization constructor. For example, the **InterruptException** includes the following constructor:  
  
```  
// "info" is the object holding the serialized object data.  
// "context" is the contextual information about the source  
// or destination.  
public InterruptException(SerializationInfo info,  
                  StreamingContext context) : base(info, context) { }  
```  
  
 For more detailed information about custom serialization, see Custom Serialization in the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] Developer's Guide.  
  
## Nested Exception Handlers and Compensation Blocks  
 In addition to serving as specialized exceptions, the custom exceptions in several places also serve as a sort flag. In the **Change** orchestration, there are two places that the Cancel operation must be rolled back.  
  
> [!NOTE]
>  You may want to read this section with the **Change** orchestration open in Visual Studio.  
  
 At the top of the orchestration, if the call to the **Cancel** orchestration fails, the **CancelCompensation** block executes and rolls back the **Cancel** transaction. If all goes well, the orchestration then calls the **Activate** orchestration.  
  
 If the **Activate** operation fails, the **Cancel** transaction must also be rolled back. However, the exception handler for the call to **Activate** knows nothing about the **Cancel** transaction. To handle this, there is an exception handler for the entire orchestration. This handler, because it contains the **Cancel** scope, knows about the **Cancel** transaction. The handler catches the exception thrown from the **Activate** scope (the **ActivateException**), rolls back the **Cancel** transaction, and then throws the exception again so that the orchestration that called the **Change** orchestration can perform any additional processing.  
  
 Notice that this design only compensates the **Cancel** if the **Activate** fails. If the **Cancel** fails and throws an exception, the **Cancel** never took place and should not be compensated.  
  
 For more information about compensation blocks and the **Compensate** shape, see [How to Configure the Compensate Shape](../core/how-to-configure-the-compensate-shape.md).  
  
## See Also  
 [Exception Handling in the Business Process Management Solution](../core/exception-handling-in-the-business-process-management-solution.md)   
 [The ExceptionHandler Orchestration](../core/the-exceptionhandler-orchestration.md)