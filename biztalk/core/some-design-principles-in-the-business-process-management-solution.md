---
title: "Some Design Principles in the Business Process Management Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "business processes, design principals"
  - "designing, design principals"
  - "process management solution tutorial, dividing business processes"
  - "patterns [process management solutions], design principals"
ms.assetid: 688b970f-8e64-4a47-bcc5-bdb9c5195902
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Some Design Principles in the Business Process Management Solution
This topic begins with general guidelines about dividing business processes into stages. It then goes on to consider the structure of some of the solution's orchestrations, assemblies, and applications in connection with these guidelines and the business requirements. For more information about the business requirements, see "Business Requirements" in [Understanding the Business Process Management Solution](../core/understanding-the-business-process-management-solution.md).  
  
## Dividing Business Processes  
 Often when considering a business process, the first impulse is to treat it as a single, monolithic process. This is not always the best design. For Southridge Video, an order is a long running business process, a process that may take up to a year to complete. In the meantime, the business process itself may change. To allow updates to the business process without disrupting in-process orders, the Southridge Video order processing is divided into stages.  
  
 Where you divide the process is critical to which parts of the process you can version, and to the types of disruptions that you allow to outstanding orders. The Southridge Video solution uses four general criteria to determine the stages:  
  
- The logical grouping of steps in the business process.  
  
- The scope of operations within an orchestration.  
  
- The elements of the process that would be useful to version, given the business process.  
  
- An orchestration should end after completing a long-term operation.  
  
  Of the four, the first and third are the most critical because there will usually be far more scopes of operations than logical groupings or obvious elements to version. Notice, however, that you do not want to end an orchestration in the middle of a scope.  
  
  If you look at the orchestration for the first stage, **CableOrder1.odx**, you'll see that it effectively ends with the request-response sequence to the facilities system. This is a good place for the stage to end because it is the part of the process that involves the actual physical work of completing the order. Having the long processing steps near the end of the orchestration guarantees that, when rehydrated, the orchestration ends quickly. This speeds up the movement of the solution as a whole to newer versions of the orchestrations.  
  
> [!NOTE]
>  Although the solution splits the process into discontinuous stages, the solution monitoring enables you to see things a continuous view through the use of BAM.  
  
## Order Action, Broker, and Manager Orchestrations  
 In addition to breaking the order processing into stages, you will also notice that each of the order actions—for example, analyzing the order, order validation, order cancellation—is in a separate orchestration. Putting each action in a separate orchestration decouples the actions from the structure of the stages. This in turn enables greater flexibility in designing and versioning the order processing stages.  
  
 The order broker and order manager are in separate orchestrations for similar reasons. The solution design enables use of multiple order managers to handle other kinds of orders. The decoupling of the broker and manager also allows for these to be in different locations. For additional details about the order broker's design, see "Why and Order Broker?" in [Processing in the OrderBroker Orchestration](../core/processing-in-the-orderbroker-orchestration.md). For the details of the order manager, see [Process Manager Logic](../core/process-manager-logic.md).  
  
## Assemblies  
 The assemblies in the solution are organized to support versioning of components and to support moving components to other servers. For example, schemas are in separate assemblies. In particular, the schemas for the order broker are in their own  assembly. This allows them to be versioned without changing other elements of the solution. It also makes it simpler to move the order broker to a separate group or server. For more information about versioning the application and schema assemblies, see [Versioning the Business Process Management Solution](../core/versioning-the-business-process-management-solution.md).  
  
## Applications  
 If you look in the BizTalk Administration Console, you can see that the built solution consists of three separate applications:  
  
- **BTSScn.BPM.OrderBrokerApp**, the application containing the order broker  
  
- **BTSScn.BPM.CableOrderApp**, the application containing the order processing components  
  
- **BTSScn.BPM.MessagingApp**, an application that collects artifacts shared by the other two applications  
  
  The tripartite structure of the solution is possible because of the ability of BizTalk applications to use artifacts in other applications within the same BizTalk group. To use another application's artifacts, you add a reference to the other application from the referring application. For information about referencing other applications, see [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).  
  
  Putting the common artifacts in a separate application enables you, potentially, to update components in only one place. The shared components can be anything, including ports. For example, the orchestrations in the solution send errors to an error reporting port. That port is in the messaging application, BTSScn.BPM.MessagingApp, where the entire solution can use it.  
  
  Structuring the solution as three applications also makes it easier to move parts of the solution onto other servers. You can convert each application and its referenced applications into an MSI file. You can then install that MSI file on another machine. For information about converting applications into MSI files, see [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).  
  
### The Test Solution  
 You will also three test applications in the BizTalk Administration Console: **BTSScn.BPM.OrderBrokerApp.Test**, **BTSScn.BPM.CableOrderApp.Test**, and **BTSScn.BPM.MessagingApp.Test**. These three applications contain only the ports for the test application and are referenced by the main applications. This structure allows for the test ports to be used by the main applications to construct a test solution while at the same time decoupling the test ports from the solution.  
  
## See Also  
 [Implementation Highlights of the Business Process Management Solution](../core/implementation-highlights-of-the-business-process-management-solution.md)   
 [Patterns in the Business Process Management Solution](../core/patterns-in-the-business-process-management-solution.md)