---
title: "Components of the Business Process Management Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "process management solution tutorial, back-end systems, process management solutions"
  - "process management solution tutorial, client applications"
  - "orchestrations, process management solutions"
  - "adapters, process management solutions"
  - "process management solution tutorial, adapters"
  - "client applications, process management solutions"
  - "process management solution tutorial, components"
  - "process management solution tutorial, orchestrations"
  - "pipelines, process management solutions"
  - "process management solution tutorial, pipelines"
  - "assemblies, process management solutions"
  - "process management solution tutorial, assemblies"
ms.assetid: e3ccebb9-b677-4c17-acd2-0f986f7bd3f0
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Components of the Business Process Management Solution
This section describes the major BizTalk Server components of the Business Process Management Solution. For information about the source files, see [File Inventory for the Business Process Management Solution](../core/file-inventory-for-the-business-process-management-solution.md).  
  
## Orchestrations  
 There are two main orchestrations: **OrderBroker** and **OrderManager**. The **OrderBroker** orchestration accepts customer requests through a Web service or in batches through FTP, and sends replies back through a Microsoft Message Queuing (MSMQ) queue. Requests go from the **OrderBroker** to the **OrderManager**. The two orchestrations are direct bound through the MessageBox database.  
  
 The **OrderManager** runs the requests through two asynchronous processing stages using the **CableOrder1** and **CableOrder2** orchestrations. Taken together, the **CableOrder1** and **CableOrder2** orchestrations represent a single business process. However, the process has been broken into two orchestrations so that stages can be changed without disrupting order processing. For more information about the design of the stages, see "Dividing Business Processes" in [Some Design Principles in the Business Process Management Solution](../core/some-design-principles-in-the-business-process-management-solution.md).  
  
 The **CableOrder1** orchestration uses the **Validate** orchestration to validate the order and to translate request codes into actions, calls the Analyze orchestration to analyze the order, and then calls the **Activate**, **Cancel**, or **Change** orchestration depending on the required action. The **CableOrder2** orchestration handles completion of the order by calling the **Complete** orchestration. Notice that **CableOrder1** and **CableOrder2** use **Call** shapes to invoke the subordinate orchestrations.  
  
> [!NOTE]
>  The **Cancel** orchestration includes a compensation block that calls the **Activate** orchestration. This ensures that the order is properly restored as part of the compensation for the cancel request.  
  
 The **CableOrder1** and **CableOrder2** orchestrations use direct binding. For more information about the direct binding of these orchestrations, see [Implementation Highlights of the Business Process Management Solution](../core/implementation-highlights-of-the-business-process-management-solution.md).  
  
 Many of the orchestrations are written so that they can be interrupted during processing using the **Interrupt** orchestration. For more information about the interrupt mechanism, see [Process Manager Logic](../core/process-manager-logic.md).  
  
## Back-end Applications  
 The Business Process Management solution uses simulations for all of the back-end applications. **CableOrder1**, **CableOrder2**, and the orchestrations they use all employ a special **OrderHandler** object. The **OrderHandler** uses .NET remoting to communicate with a simulation of an order management system. The **CableProvisioningSystemClient** and **BTSScnBPMProvisioning** (the **CableProvisioningSystemServer** project) assemblies simulate the front and back ends of the order managing system, respectively.  
  
 The solution uses a Windows forms application, **BSTScnBPMFacilities** (the **FacilitiesSimulator** project), to simulate the MSMQ server that handles the facilities requests.  
  
 In addition to these components, the orchestrations also make entries in a SQL Server database to maintain a history of orders and their processing.  
  
## Pipelines  
 The solution uses only standard default pipelines configured through the BizTalk Administration console or binding files. The pipelines do, however, make extensive use of per-instance configuration. The receive port for orders sent by FTP uses per-instance configuration to configure the envelope. For more information about per-instance configuration, see [How to Deploy Pipelines](../core/how-to-deploy-pipelines.md).  
  
## Custom Adapter  
 The solution uses a custom adapter, the **OpsAdapter**, to process some errors detected in the **OrderManager** and **ErrorHandler** orchestrations. The solution uses the adapter on ports for which error reporting is specified. The adapter takes the errors and sends them on to the operations system. For more information about error reporting, see [Using Failed Message Routing](../core/using-failed-message-routing.md).  
  
## Client Application  
 The solution includes an ASP.NET Web page backed by a C# program, **CSRMain.aspx**, to simulate the customer service system.  
  
## Other Assemblies  
 The solution uses two additional assemblies, **Schemas** and **Utilities**. The **Schemas** assembly defines the messages the solution uses for communicating among the different orchestrations such as the **Interrupt** message. The solution also uses several .NET messages defined in the **SchemaClasses** assembly.  
  
 The **Utilities** assembly includes utility classes and methods to help handle messages, to define an exception type specific to the solution, to read configuration values from the SSO secret store, and to help with error handling. The assembly also includes the **Recaller** object.  
  
 Other assemblies include map and schema assemblies such as **OrderBrokerMaps**, **OrderBrokerSchemas**, **Maps**, **MessagingSchemas**, and **SchemaClasses**.  
  
 The **ServiceLevelTracking** assembly contains the common artifacts used with BAM to track orders and processing. Order processing actions used by the stages are in the **CableOrderActions** assembly.  
  
## See Also  
 [Patterns in the Business Process Management Solution](../core/patterns-in-the-business-process-management-solution.md)   
 [Processing in the Business Process Management Solution](../core/processing-in-the-business-process-management-solution.md)   
 [Implementation Highlights of the Business Process Management Solution](../core/implementation-highlights-of-the-business-process-management-solution.md)   
 [Monitoring the Business Process Management Solution with BAM](../core/monitoring-the-business-process-management-solution-with-bam.md)   
 [Versioning the Business Process Management Solution](../core/versioning-the-business-process-management-solution.md)   
 [Business Process Management Solution Reference](../core/business-process-management-solution-reference.md)   
 [Developing a Business Process Management Solution](../core/developing-a-business-process-management-solution.md)   
 [File Inventory for the Business Process Management Solution](../core/file-inventory-for-the-business-process-management-solution.md)