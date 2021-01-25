---
description: "Learn more about: Processing in the Order Processing Stages"
title: "Processing in the Order Processing Stages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 698005da-1ba8-4972-83db-f5ae45fd6a83
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Processing in the Order Processing Stages
The Business Process Management solution includes two stages, the **CableOrder1** and **CableOrder2** orchestrations, that perform the order processing actions. For more information about how the order process was divided into stages, see [Number of Processing Stages](../core/number-of-processing-stages.md).  
  
 Both processing stages begin when they receive an order message and both reply with a status message to the **OrderManager** orchestration once they have started. Similarly, both send a message back to the **OrderManager** to indicate whether the stage completed or terminated with an error. For details about the connection between the **OrderManager** orchestration and the processing stages, see [Inverse Direct Partner Binding](../core/inverse-direct-partner-binding.md).  
  
 Both processing stages use self-correlating, dynamic ports to send information back to the **OrderManger**. With dynamic ports, the orchestrations copy the port address from the message to send port.  
  
 All of the order messages the processing stages receive are the normalized, canonical order messages created in the **OrderBroker**.  
  
> [!NOTE]
>  Because of the length of the **CableOrder1** and **CableOrder2** orchestrations, you may want to read this section with the orchestrations open in Microsoft Visual Studio.  
  
## The CableOrder1 Orchestration  
 The **CableOrder1** orchestration starts when it receives an order message. It then copies the reply address from the message to the stage completion port. Next, it constructs an acknowledgement message and sends it as a response to the **BeginStagePort** port, and then saves the routing information in a local variable.  
  
 The orchestration next gets the configuration information from SSO. For more information about how the solution uses SSO, see [Using SSO Efficiently in the Business Process Management Solution](../core/using-sso-efficiently-in-the-business-process-management-solution.md).  
  
 The orchestration then creates an instance of the **OrderHandler** object to communicate with the backend processes, checks the validity of the message, analyzes the message, determines the service type, and which action to take. Depending on the action to take, it calls one of the order action orchestrations **Activate**, **Change**, or **Cancel** and passes the **OrderHandler** object to the orchestration.  
  
 The **CableOrder1** orchestration then checks for an interrupt, sends a message to the facilities group and waits to hear back. If the orchestration gets a message back from the facilities group, it continues processing. Otherwise, if there is an interrupt, the orchestration throws an interrupt exception.  
  
 The orchestration finishes by constructing a completion message and sending it through the **StageCompletion** port.  
  
## The CableOrder2 Orchestration  
 The CableOrder2 orchestration performs the same starting steps as the CableOrder1 orchestration for the routing information, SSO configuration information, and creating an instance of the **OrderHandler** object.  
  
 The orchestration then checks for an interrupt and passes the **OrderHandler** object in a call to the **Complete** orchestration. Next, the orchestration creates an order status message, updates the order history, and sends a completion message through the **StageCompletion** port.  
  
## See Also  
 [Versioning the Business Process Management Solution](../core/versioning-the-business-process-management-solution.md)   
 [Processing in the Business Process Management Solution](../core/processing-in-the-business-process-management-solution.md)
