---
title: "Using Correlations in Orchestrations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, orchestrations"
  - "messages, correlation sets"
  - "correlation sets"
  - "orchestrations, messages"
  - "messages, validating"
ms.assetid: d919afa9-bada-406a-bf4b-7b46c831c6d5
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Correlations in Orchestrations
Correlation is the process of matching an incoming message with the appropriate instance of an orchestration. For example, orchestration sends out of a message and receives the response or responses back into the same orchestration. There are three correlated messages exchange patterns:  
  
- Traditional handshake  
  
- Sequential convoy  
  
- Parallel convoy  
  
  In the traditional handshake pattern, handshakes exist between the exchanges of the messages among the orchestrations or business processes, and you can achieve the handshakes by defining correlation sets in the orchestrations where a correlation set is a list of promoted properties with specific values that you use to route messages to a specific orchestration instance.  
  
  If, for example, your orchestration is designed to issue a purchase order, receive an invoice, and send out the payment, you need to be sure that the invoice message is received by the same orchestration instance that the corresponding purchase order was sent from since numbers of purchase orders may be processed at the time. In this example, the purchase order identification number can be used as a parameter in the correlation set for correlating the purchase order message and the invoice message. The following is the scenario flow for this example,  
  
1. The Orchestration A sends out the purchase order message to the Orchestration B. Before sending out the purchase order message, the correlation set is initialized.  
  
2. In the Orchestration B, in which processes the purchase order, generates and sends back the invoice, the first Receive shape follows the same correlation set to receive the purchase order message.  
  
3. After processing the purchase order message, when sending back the invoice message to the Orchestration A, the same correlation set is also followed.  
  
4. In the Orchestration A, at the Receive shape which receives the invoice message back from the orchestration B, the same correlation set is also followed to ensure that receiving the correlated invoice message based on the predefined correlation set.  
  
   The sequential convoy and parallel convoy patterns exist in the world any time multiple single items must be related together in order to achieve something that the individual item cannot accomplish by itself. For more information, see [Working with Convoy Scenarios](../core/working-with-convoy-scenarios.md).  
  
   In addition to the correlated message exchange patterns, there are two types of correlations in orchestration:  
  
- Manual correlation  
  
- Automatic correlation  
  
  In the manual correlation scenario, you manually configure the orchestrations to initialize and follow the correlation set to associate the messages with proper instances. In the automatic correlation scenario, the messaging engine will correlate the messages with the instances for you, for example, when you set up Request-Response port or Self-Correlating port in your orchestrations.  
  
  You must use correlation whenever your orchestration does not have an explicit way of associating a message with an instance, such as an activate receive, a request-response, or a self-correlating port.  
  
## Examples of Using Correlations  
  
-   [PartyResolution (BizTalk Server Sample)](../core/partyresolution-biztalk-server-sample.md)  
  
-   Download the SDK sample "Correlating Messages with Orchestration Instances" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
-   Download the SDK sample "Parallel Convoy" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
## In This Section  
  
-   [Correlation Sets](../core/correlation-sets.md) 
  
-   [Correlation Types](../core/correlation-types.md) 
  
-   [How to Add and Remove Correlation Sets](../core/how-to-add-and-remove-correlation-sets.md) 
  
-   [How to Configure Correlation Sets](../core/how-to-configure-correlation-sets.md)  
  
-   [How to Configure Correlation Types](../core/how-to-configure-correlation-types.md)  
  
-   [Working with Convoy Scenarios](../core/working-with-convoy-scenarios.md)  
  
## See Also  
 [How to Use Self-Correlating Direct Bound Ports](../core/how-to-use-self-correlating-direct-bound-ports.md)