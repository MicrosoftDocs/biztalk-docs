---
title: "Inverse Direct Partner Binding | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "bindings, partners"
  - "process management solution tutorial, partner binding"
ms.assetid: 4cf8717a-2098-46f4-8f58-9d05fb562e2a
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Inverse Direct Partner Binding
The Business Process Management solution is designed so that you can change the order processing stages without stopping the application. In order to decouple the processing stages (**CableOrder1**, **CableOrder2**) from the process manager (**OrderManager**), the solution uses a different technique for binding ports among these orchestrations.  
  
 In the usual form of binding, direct binding, the **OrderManager** orchestration would use the process stage orchestration as the value for the Partner Orchestration Port property. In direct binding like this the **OrderManager** orchestration depends on the strong names (which include the versions) of the process stages. This makes it impossible to alter the process stages without re-deploying the **OrderManager** orchestration. For more information about direct binding, see [Port Bindings](../core/port-bindings.md). Direct Binding might be illustrated this way:  
  
 ![Diagram of Inverse Direct Partner Binding](../core/media/bpm-inverse-direct-binding.gif "BPM_Inverse_Direct_Binding")  
  
 In inverse direct partner binding, the receiving orchestration specifies the binding, rather than the originating orchestration. The port on the **OrderManager** is simply bound to itself. That is, the port on the **OrderManager** is specified for the **PartnerOrchestrationPort** property. However, the process stage orchestrations use the appropriate **OrderManager** port as the value for the **PartnerOrchestrationPort** property. This decouples the **OrderManager** from the versions of the process stage orchestrations and allows them to be changed without redeploying the **OrderManager**. Direct binding would not allow this decoupling. Inverse direct partner binding might be shown this way:  
  
 ![Diagram of Direct Binding](../core/media/bpm-direct-binding.gif "BPM_Direct_Binding")  
  
> [!NOTE]
>  Inverse direct binding also allows for communicating with partner orchestrations in a distribution-list like way. The **OrderManger** can use a single port to communicate with all stages. This enables you to add and remove stages without redesigning the orchestration.  
  
## See Also  
 [Implementation Highlights of the Business Process Management Solution](../core/implementation-highlights-of-the-business-process-management-solution.md)   
 [Process Manager Logic](../core/process-manager-logic.md)