---
title: "Event Signaling1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe011714-d9a7-4032-8300-643f8dbaa07b
caps.latest.revision: 3
---
# Event Signaling
The device driver notifies the SNALink whenever an event occurs (such as a frame being received from the line) by setting an event.  
  
 The SNALink provides the driver with a handle to this event (or semaphore) at the start of day by issuing an IOCTL call of type **SET_EVENT_HANDLE**.