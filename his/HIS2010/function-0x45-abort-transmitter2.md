---
title: "Function 0x45: Abort Transmitter2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1bb94ce0-2cf0-4ded-8ca2-468218ad61f8
caps.latest.revision: 3
---
# Function 0x45: Abort Transmitter
The SNALink calls this function to clear down the driver's transmitter.  
  
## Remarks  
 This request causes the driver to stop the current frame transmission and to flush its internal buffers of any further data pending transmission. In two-wire configurations, the driver should also drop RTS.