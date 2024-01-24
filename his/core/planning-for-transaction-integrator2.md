---
description: "Learn more about: Planning for Transaction Integrator"
title: "Planning for Transaction Integrator"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Planning for Transaction Integrator

## Overview
Before installing and using Transaction Integrator (TI), determine whether your mainframe-based transaction programs (TPs) can be used with TI and whether any of them need modification. Answer the following three questions to find out whether TI can invoke your TP:  
  
- Is the TP irretrievably terminal-oriented, or can you expose a request-response interface?  
  
- What programming model does the TP need?  
  
- Does the TP use data types that TI supports?  
  
  To use TI to invoke a mainframe-based transaction program (TP), you must separate the business logic from the presentation logic in the TP. TI uses the request-response model; it does not support conversational or pseudo-conversational transactions. The TP must support the so-called ping-pong request-reply mode.  
  
  Although TI does not support screen scraping, it does support eight other communication models. Some CICS and most IMS transactions that expose terminal interface can also be invoked using one of the eight supported models. For example, a CICS transaction might be terminal-oriented but still have the business logic partitioned in a separate link model transaction for load balancing or maintainability.  
  
## Next steps
 [Communication Models](../core/communication-models2.md)   
 [CICS and VTAM Sample Definitions for LU 6.2](../core/cics-and-vtam-sample-definitions-for-lu-6-21.md)   
