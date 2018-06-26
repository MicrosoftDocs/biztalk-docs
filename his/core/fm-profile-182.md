---
title: "FM Profile 182 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 11a24127-a0ab-4164-93f7-403d89d1aacf
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# FM Profile 18
Function management (FM) Profile 18 is supported on primary logical unit-secondary logical unit (PLU-SLU) sessions using LU 0. This profile uses the following session rules:  
  
- PLU and SLU use immediate response mode.  
  
- PLU and SLU support the following data flow control (DFC) commands (an asterisk [*] indicates commands permitted by the FM profile that are never sent by [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)]):  
  
  -   **CANCEL**  
  
  -   **SIGNAL**  
  
  -   **LUSTAT**  
  
  -   **BIS** and **SBI** (allowed only if brackets are used)  
  
  -   **CHASE***  
  
  -   **BID** and **RTR** (allowed only if brackets are used)  
  
- Length-checked compression is allowed.  
  
  The following FM Usage fields define the options for Profile 18:  
  
- Chaining use (PLU and SLU)  
  
- Request control mode selection (PLU and SLU)  
  
- Chain response protocol (PLU and SLU)  
  
- FMH-1 SCB Compression indicator (PLU and SLU)  
  
- Send EB indicator (PLU and SLU)  
  
- FM header usage  
  
- Brackets usage and reset state  
  
- Bracket termination rule  
  
- Alternate Code Set Allowed indicator  
  
- Normal-flow send/receive mode  
  
- Recovery responsibility  
  
- Contention winner/loser  
  
- Half-duplex flip-flop reset states  
  
## See Also  
 [Transmission Service and Function Management Profiles](../core/transmission-service-and-function-management-profiles1.md)