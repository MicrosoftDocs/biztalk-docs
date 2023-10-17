---
description: "Learn more about: Transmitter Interfaces"
title: "Transmitter Interfaces | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ffa6db3b-739e-438c-b410-8823a20eed82
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Transmitter Interfaces
In addition to the mandatory adapter interfaces, transmit (send) adapters, need to implement either **IBTTransmitter** if they are non-batched or **IBTBatchTransmitter** if they are batched.  
  
 The following figure shows the interfaces that batched and non-batched send adapters need to implement.  
  
 ![Diagram showing the mandatory, optional, and choice interfaces that batched and non-batched send adapters need to implement.](../core/media/transmitterinterfaces.gif)
