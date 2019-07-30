---
title: "Synchronous Dumb Card Interface1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe78b2b6-afd9-4a4b-b91f-c96079e2a3b3
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Synchronous Dumb Card Interface
This section describes the interface to the synchronous dumb card device driver used by the Synchronous Data Link Control (SDLC) and X.25 SNALinks that Microsoft Host Integration Server supplies. The interface provides a simple but flexible mechanism for transferring frames of data through a dumb synchronous communications card (such as the IBM MPCA card).  
  
 This interface is intended primarily for independent hardware vendors (IHVs) who want to provide drivers for their own dumb cards that are directly compatible with SDLC and X.25 SNALinks. It can also be used by Independent Hardware Vendors (IHVs) who intend to write their own SNALinks and want to ensure that their drivers conform to the standard Host Integration Server model.  
  
## In This Section  
  
-   [Driver Interface](../core/driver-interface2.md)  
  
-   [I/O Request Packets](../core/i-o-request-packets1.md)