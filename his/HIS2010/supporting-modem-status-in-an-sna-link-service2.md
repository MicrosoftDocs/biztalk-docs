---
title: "Supporting Modem Status in an SNA Link Service2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2a478445-9ef5-4841-8d01-0d678d44a3f8
caps.latest.revision: 3
---
# Supporting Modem Status in an SNA Link Service
The implementation of a link service that supports the modem status requires the following:  
  
-   A call to the SNA Modem interface to initialize the SNA Modem data structures.  
  
-   Modification of the SNA Modem structures as the status changes, as reported by the **DevIoctl** calls.  
  
 Independent hardware vendors (IHVs) who use the Microsoft[!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] SDLC link service and who fully implement the SNADIS interface do not need to make any changes to use the modem status feature. However, IHVs should check that the status returned by **DevIoctl** calls from their device driver conforms to the requirements described later.  
  
 IHVs who provide both the device driver and link service need to implement the code in their link service that initializes the SNA Modem API and updates the modem status information.