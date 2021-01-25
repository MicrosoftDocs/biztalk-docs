---
description: "Learn more about: FILLER Optimization"
title: "FILLER Optimization1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8ea50285-0283-4c63-be03-bc0afb30a314
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# FILLER Optimization
The Transaction Integrator (TI) run-time environment optimizes buffers sent to the host by not sending the bytes corresponding to FILLER that appear at the end of the input data declaration.  
  
 In a CICS LU 6.2 environment, use both the MAXLENGTH and NOTRUNCATE options on the RECEIVE statement when the TI run-time environment receives an input area that contains FILLER as the last data item description. However, this requirement does not apply to CICS LINK and IMS transaction programs.  
  
## See Also  
 [Filler](../core/filler1.md)
