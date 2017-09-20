---
title: "Using the Order Handler Object to Communicate with Backend Systems | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IOrderHandler interface"
  - "process management solution tutorial, IOrderHandler interface"
ms.assetid: b9fe4120-bf2a-4d15-a34b-6b98f026b984
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using the Order Handler Object to Communicate with Backend Systems
There are many ways in which the business process management solution could communicate with the legacy back-end order system, the cable provisioning system that receives the final orders. The solution uses the .NET remoting facilities found in Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] to communicate with the provisioning system.  
  
 The solution uses a common technique of using an interface to define the access object to the back-end system. By putting the interface in a separate assembly the client assembly can have access to the remote object without having to have access to the compiled assembly.  
  
 The **IOrderHandler** interface defines the methods to communicate with the backend order system. The interface includes methods for analyzing, activating, canceling, and completing orders. It also provides a method for identifying the service type, a method needed when an order is canceled.  
  
 The **CableOrder1**, **CableOrder2**, and satellite orchestrations use the **OrderHandlerWrapper** object that implements **IOrderHandler**. The **OrderHandlerWrapper** object, in turn, invokes a remote instance of an **OrderHandler** object provided by the **CableProvisioningSystemServer** executable. Using the wrapper object meets the business requirement of using .NET remoting to communicate with the back-end order system while, at the same time, enabling use of the retry features of the exception handling components.  
  
 Because one must be able to serialize every object referenced in an orchestration, the **OrderHandlerWrapper** can also be serialized. Using the **OrderHandlerWrapper** isolates the serialization code from the orchestrations.  
  
 If you look at the code, you'll se that the **OrderHandlerWrapper** object explicitly implements the **ISerializable** interface. The object must handle its own serialization because it uses a non-default constructor.  
  
 Using .NET remoting to communicate with the backend system is more efficient than using messaging. On the other hand, it binds the orchestrations more tightly to the back-end system than a pure messaging solution might. Using .NET remoting also prevents the solution from taking advantage of the built-in BizTalk Server features for retrying requests.  
  
## See Also  
 [Implementation Highlights of the Business Process Management Solution](../core/implementation-highlights-of-the-business-process-management-solution.md)   
 [Process Manager Logic](../core/process-manager-logic.md)