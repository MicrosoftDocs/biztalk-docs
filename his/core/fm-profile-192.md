---
title: "FM Profile 192 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1ed284c3-ec51-47e1-af33-edd47b1f9835
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# FM Profile 19
Function management (FM) Profile 19 is supported on primary logical unit-secondary logical unit (PLU-SLU) sessions using LU 6.2. This profile specifies the following session rules:  
  
- PLU and SLU use immediate request mode.  
  
- PLU and SLU use immediate response mode.  
  
- Multiple RU chains are allowed.  
  
- PLU and SLU requests indicate definite or exception response.  
  
- No compression is used.  
  
- Brackets are used.  
  
- FM headers (types 5, 7, and 12 only) are allowed.  
  
- Conditional termination for brackets, specified by conditional end bracket (CEB),is used.  
  
- PLU and SLU may send CEB.  
  
- Normal-flow send/receive mode is half-duplex flip-flop.  
  
- Half-duplex flip-flop reset state is SEND for PLU.  
  
- Symmetric error responsibility.  
  
- Contention winner/loser is negotiated at BIND time.  
  
- PLU and SLU support the following data flow control (DFC) commands:  
  
  -   **SIGNAL**  
  
  -   **LUSTAT**  
  
  -   **BIS**  
  
  -   **RTR**  
  
- The following combinations of RQE, RQD, CEB, and CD are allowed on end-chain Russ  
  
  ||||  
  |-|-|-|  
  |RQE|CD|CEB|  
  |RQD2|CD|CEB|  
  |RQD3|CD|CEB|  
  |RQE1|CD|CEB|  
  |RQD|CD|CEB|  
  
  The only option for Profile 19 is contention winner/loser.  
  
## See Also  
 [Transmission Service and Function Management Profiles](../core/transmission-service-and-function-management-profiles1.md)