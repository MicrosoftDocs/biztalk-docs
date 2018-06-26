---
title: "How to Create Receive Subscriptions at Invoked Orchestrations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3423309a-cb5a-40a5-9582-6ee3ac82b538
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create Receive Subscriptions at Invoked Orchestrations
Although you can pass messages as parameters through the **Start Orchestration** shape when you start an orchestration, in some scenarios you may want to send messages from the caller orchestration to the invoked orchestration after the invocation. For example, you may not know what messages you want to pass at the time of invocation, or other orchestrations may need to send messages to the invoked orchestration dynamically.  
  
 The way to send a message to an invoked orchestration is to pass in a correlation so that the invoked orchestration can create the subscription that the correlation helps define and then receive the message by using that subscription. However, you cannot simply pass in a correlation and expect the invoked orchestration to create the subscription based on the correlation and receive a message on the subscription. If you use that approach, the messages you send from the caller orchestration to the invoked orchestration will result in the error, "The published message could not be routed because no subscribers were found." This is because of the following:  
  
- There is a race condition in the invoked orchestration.  
  
- There is no commit point for the invoked orchestration to send the subscription to the MessageBox database for routing so that it can receive the messages.  
  
  A way to resolve this problem is to perform the following steps:  
  
1. In the caller orchestration, you have an activate receive to receive the message. After you receive the message in the caller orchestration, initialize the correlation set, and then pass the correlation set and a self-correlating receive direct-bound port through the **Start Orchestration** shape. The port that you pass in becomes a send port in the invoked orchestration, and you will use it to send the message back to synchronize with the caller orchestration.  
  
2. In the invoked orchestration, send a message back to the caller orchestration through the self-correlating port. This synchronizes with the caller orchestration to prevent race conditions and to provide a commit point while creating the receive subscription to the MessageBox for routing in the invoked orchestration.  
  
3. The caller orchestration receives the message through the self-correlating port and synchronizes with the invoked orchestration. Note that self-correlating port receives do not need correlation followers. You can now safely send messages from the caller orchestration to the invoked orchestration, and the invoked orchestration will receive the messages based upon the correlation.  
  
   Although the preceding approach can achieve the goal, a better approach is to pass in the message that initializes the correlation on which you want to receive upon. When you are synchronizing a caller orchestration with an invoked orchestration through a self-correlating port, we recommend that you always pass in the message that you need for initializing the correlations. The following steps provide the most reliable and highest-performance approach:  
  
4. In the caller orchestration, you have an activate receive to receive the message. After you receive the message, pass a message and a self-correlating receive direct-bound port through the **Start Orchestration** shape. The message you pass in will be used to initialize the correlation in the invoked orchestration. The port that you pass in becomes a send port in the invoked orchestration, and you will use it to send the message back to synchronize with the caller orchestration.  
  
5. In the invoked orchestration, initialize the correlation and send a message back to the caller orchestration. This synchronizes with the caller orchestration to prevent race conditions and to provide a commit point while creating the receive subscription to the MessageBox for routing in the invoked orchestration.  
  
6. The caller orchestration receives the message through the self-correlating port and synchronizes with the invoked orchestration. Note that the self-correlating port receives do not need correlation followers. You can now safely send messages from the caller orchestration to the invoked orchestration, and the invoked orchestration will receive the messages based upon the correlation.  
  
## See Also  
 [Using Correlations in Orchestrations](../core/using-correlations-in-orchestrations.md)   
 [How to Use Self-Correlating Direct Bound Ports](../core/how-to-use-self-correlating-direct-bound-ports.md)