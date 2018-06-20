---
title: "Sequential Convoys | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "convoy sets"
  - "correlation sets, sequential receive tasks"
ms.assetid: f05ff42c-2236-42a3-8166-19700e0c3d97
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Sequential Convoys
A sequential convoy enables multiple single messages to join together to achieve a required result. A sequential convoy is a set of related messages that have a predefined order. Although the messages do not have to be exactly the same, BizTalk Server must receive them in a sequential order.  
  
 For example, suppose that an online retail company receives new orders from direct clients and from dealers throughout the course of the day. All orders received before 2:00 PM must go to the warehouse in a single batch, and the sequence of the receipt of the orders must be preserved. This enables earlier orders to have priority in case any items are out of stock in the warehouse. You build this batch order by assembling all orders for the day in a single file that has batch header information. At 2:00 PM, all orders for the day go to the warehouse for processing. All orders received after 2:00 PM are put into a new batch for processing on the following day.  
  
 The preceding scenario is an example of a business process that requires sequential convoy processing of incoming messages. The business requirements state that all single orders received before 2:00 PM for a specific day should batch together. This requires the first message received to start a new orchestration instance and initialize a correlation set. At that point, all other orders received of that message type route to the already-running orchestration instance. To accomplish this, you position a **Listen** shape (containing a **Receive** shape and a **Delay** shape) inside a **Loop** shape. After reaching the delay, the loop ends. This allows for the receipt of an unknown number of orders in the same business process.  
  
## Implementing Sequential Convoys  
 You can implement sequential convoys by using the "sequential correlated receives" messaging design pattern in BizTalk Server. Sequential correlated receives are receives that are correlated to previous receives.  
  
 Convoy processing takes place for cases in which the correlation sets for a receive are initialized by another receive.  
  
 For receives that require convoy processing, the following restrictions apply:  
  
- The correlation sets that constitute a sequential convoy set for a particular receive must be initialized by one preceding receive.  
  
- The port for a receive that requires sequential convoy processing must be the same as the port for the receive initializing the convoy set. Cross-port convoys are not supported.  
  
- Message types for a receive that requires convoy processing must match the message type for the receive initializing the convoy set, unless the receive statement is operating on an ordered delivery port.  
  
- All receives participating in a sequential convoy must follow all the correlation sets that are initialized (or followed) by the initializing receive, unless operating on an ordered delivery port.  
  
- If a sequential convoy is initialized by an activate receive statement, then the activate receive cannot have a filter expression unless operating on an ordered delivery port.  
  
- If a sequential convoy is initialized by an activate receive, the following receives cannot be inside a nested orchestration.  
  
  For an example of sequential convoy implementation, see [Aggregator (BizTalk Server Sample)](../core/aggregator-biztalk-server-sample.md).  
  
## See Also  
 [Working with Convoy Scenarios](../core/working-with-convoy-scenarios.md)   
 [Parallel Convoys](../core/parallel-convoys.md)