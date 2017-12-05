---
title: "Work Manager1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8dd04cdb-02a6-4fe7-bc0e-dfa3a57ae343
caps.latest.revision: 3
---
# Work Manager
When no work is currently outstanding, the Base thread of execution sleeps, waiting for an event or for a maximum period of five seconds. SNALinks should signal the Base when an event occurs (such as data arriving on the link) by setting the Base global event. A handle to this event is passed on the [SNALinkInitialize](../core/snalinkinitialize1.md) call.  
  
 When the Base is rescheduled, it calls the SNALink work manager function [SNALinkWorkProc](../core/snalinkworkproc2.md). This function should handle any link events that have occurred.  
  
 A common use of this function is in an SNALink where there is a single thread that handles the protocol of the link and also multiple threads suspended on synchronous calls to a driver read function. When data is received from the link, it is placed on an internal queue, and the driver sets the global Base event. This causes the Base to be scheduled, and **SNALinkWorkProc** is called. **SNALinkWorkProc** then removes messages from the queues and passes them to the Base to be sent to the local node.