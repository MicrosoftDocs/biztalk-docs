---
description: "Learn more about: Transmitter Interfaces"
title: "Transmitter Interfaces"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Transmitter Interfaces
In addition to the mandatory adapter interfaces, transmit (send) adapters, need to implement either **IBTTransmitter** if they are non-batched or **IBTBatchTransmitter** if they are batched.  
  
 The following figure shows the interfaces that batched and non-batched send adapters need to implement.  
  
 ![Diagram showing the mandatory, optional, and choice interfaces that batched and non-batched send adapters need to implement.](../core/media/transmitterinterfaces.gif)
