---
title: "Dispatcher (SNADIS)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3324afc5-33fd-4b82-80fe-b79e6e097083
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Dispatcher (SNADIS)
Whenever a Base event occurs, the Base calls the link support code dispatcher function [SNALinkDispatchProc](./snalinkdispatchproc2.md) to handle the event. The term Base event in this context means:  
  
- A message arriving from a local 2.1 node.  
  
- A Base timer tick occurring—this relatively slow event happens approximately every five seconds.  
  
- Losing contact with a local 2.1 node (for example, the machine being powered down).  
  
  The **SNALinkDispatchProc** function should examine parameters passed to it by the Base to determine why it has been called (for details, see [Sample Code for SNALinkDispatchProc](../core/sample-code-for-snalinkdispatchproc2.md)) and call an appropriate function to handle the event. When the event has been processed, control returns to the Base scheduler.