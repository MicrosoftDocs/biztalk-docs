---
description: "Learn more about: Event Signaling"
title: "Event Signaling2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Event Signaling
The device driver notifies the SNALink whenever an event occurs (such as a frame being received from the line) by setting an event.  
  
 The SNALink provides the driver with a handle to this event (or semaphore) at the start of day by issuing an IOCTL call of type **SET_EVENT_HANDLE**.
