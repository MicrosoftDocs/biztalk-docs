---
title: "FM Profile 01 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ffad5d01-36ae-468d-99fe-8eed6cbffb74
caps.latest.revision: 3
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
 [Transmission Service and Function Management Profiles](../HIS2010/transmission-service-and-function-management-profiles2.md)