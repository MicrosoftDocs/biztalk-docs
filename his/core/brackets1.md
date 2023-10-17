---
description: "Learn more about: Brackets"
title: "Brackets1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Brackets
This section primarily describes the bracket protocols between the local node and an application for a session supporting half-duplex flip-flop with brackets.  
  
 The local node enforces no bracket protocols for full-duplex sessions. Therefore, messages with begin bracket (BB) are not presented as **Status-Control(BID)** messages, and there are no **Status-Session(BETB)** messages.  
  
 The management of this protocol for a generalized application is complex, and there is a significant amount of code in the local node to simplify the application's perception of the protocol. An application is only aware of two states:  
  
- In-bracket  
  
- Between-bracket  
  
  The local node, in addition to the states of in-bracket and between-bracket, maintains transient states with a large state transition matrix, or finite-state machine, governing the half-session's state at a particular time.  
  
## In This Section  
  
-   [Bracket Initiation](../core/bracket-initiation1.md)  
  
-   [Bracket Termination](../core/bracket-termination1.md)
