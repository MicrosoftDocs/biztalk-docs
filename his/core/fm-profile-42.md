---
title: "FM Profile 42 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1269a058-1f6e-41ea-a0eb-1febbd71592b
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# FM Profile 4
Function management (FM) Profile 4 is supported on primary logical unit-secondary logical unit (PLU-SLU) sessions using LU types 0 or 1. This profile uses the following session rules:  
  
- PLU and SLU use immediate response mode.  
  
- PLU and SLU support the following data flow control (DFC) commands (an asterisk [*] indicates commands permitted by the FM profile that are never sent by [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)]):  
  
  -   **CANCEL**  
  
  -   **SIGNAL**  
  
  -   **LUSTAT**  
  
  -   **QEC**  
  
  -   **QC**  
  
  -   **RELQ**  
  
  -   **CHASE***  
  
  -   **SHUTD**  
  
  -   **SHUTC**  
  
  -   **RSHUTD***  
  
  -   **BID** and **RTR** (allowed only if brackets are used)  
  
- Length-checked compression allowed  
  
  The following FM Usage fields define the options for Profile 4:  
  
- Chaining use (PLU and SLU)  
  
- Request control mode selection (PLU and SLU)  
  
- Chain response protocol (PLU and SLU)  
  
- FMH-1 SCB (String Control Byte) Compression indicator (PLU and SLU)  
  
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