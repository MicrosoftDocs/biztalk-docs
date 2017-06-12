---
title: "Using BizTalk Server from TIBCO Rendezvous to Receive Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, receiving"
  - "receiving messages"
  - "memory use"
ms.assetid: 4eee9c3a-2966-4d5f-ba49-201bb488458c
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using BizTalk Server from TIBCO Rendezvous to Receive Messages
Microsoft BizTalk Adapter for TIBCO Rendezvous dispatches events from a queue on multiple threads. A BizTalk Server receive location is associated with one TIBCO Rendezvous event queue and its pool of dispatcher threads.  
  
## Memory Use and Errors  
 While processing events, the adapter keeps an eye on used resources. If memory use goes above the high-watermark, the adapter stops dispatching events until it reaches the low-watermark memory consumption. Note that this might result in TIBCO Rendezvous messages being missed for non certified messages (a TIBCO RV consumer has 60 seconds to remove messages from a queue). This data loss is reported as an error. If the adapter receives a TIBCO Rendezvous system advisory NO_MEMORY message, messages have already been lost.  
  
 BizTalk Adapter for TIBCO Rendezvous maintains a state, and it executes tasks differently based on that state. If the BizTalk Message Engine reports an error, and the adapter is configured to be a certified listener, it reports the error to TIBCO Rendezvous so that it can resubmit the message.  
  
## See Also  
 [TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md)   
 [Creating TIBCO Rendezvous Receive Handlers](../core/creating-tibco-rendezvous-receive-handlers.md)