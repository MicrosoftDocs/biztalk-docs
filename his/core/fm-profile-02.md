---
title: "FM Profile 02 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ee39d5cd-3a45-444c-bae9-418ba184cd60
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# FM Profile 0
Function management (FM) Profile 0 is supported on SSCP-PU and SSCP-SLU sessions. This profile specifies the following session rules:  
  
-   SSCP, PU, and SLU use immediate request mode and immediate response mode.  
  
-   Only single-RU chains are allowed.  
  
-   All chains require definite response.  
  
-   No compression.  
  
-   No data flow control (DFC) RUs.  
  
-   No function management (FM) headers.  
  
-   No brackets.  
  
-   No alternate code.  
  
-   Normal flow send/receive mode is half-duplex contention.  
  
-   Secondary wins contention.  
  
-   SSCP is responsible for recovery.  
  
## See Also  
 [Transmission Service and Function Management Profiles](../core/transmission-service-and-function-management-profiles1.md)