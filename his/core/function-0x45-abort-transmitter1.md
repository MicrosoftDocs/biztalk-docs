---
description: "Learn more about: Function 0x45: Abort Transmitter"
title: "Function 0x45: Abort Transmitter1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Function 0x45: Abort Transmitter
The SNALink calls this function to clear down the driver's transmitter.  
  
## Remarks  
 This request causes the driver to stop the current frame transmission and to flush its internal buffers of any further data pending transmission. In two-wire configurations, the driver should also drop RTS.
