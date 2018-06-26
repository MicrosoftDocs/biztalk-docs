---
title: "FM Profile 31 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cfecebd0-e3c3-4cea-b64a-16edc4255197
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# FM Profile 3
Function management (FM) Profile 3 is supported on primary logical unit-secondary logical unit (PLU-SLU) sessions using LU types 0, 1, 2, or 3. This profile specifies the following session rules:  
  
- PLU and SLU use immediate response mode.  
  
- PLU and SLU support the following data flow control (DFC) commands (an asterisk [*] indicates commands permitted by the FM profile that are never sent by [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)]):  
  
  -   **CANCEL**  
  
  -   **SIGNAL**  
  
  -   **LUSTAT** (SLU-PLU only)  
  
  -   **CHASE***  
  
  -   **SHUTD**  
  
  -   **SHUTC**  
  
  -   **RSHUTD***  
  
  -   **BID** and **RTR**  
  
  The following FM Usage fields define the options for Profile 3:  
  
- Chaining use (PLU and SLU)  
  
- Request control mode selection (PLU and SLU)  
  
- Chain response protocol (PLU and SLU)  
  
- Compression indicator (PLU and SLU)  
  
- Send EB indicator (PLU and SLU)  
  
- FM header usage  
  
- Bracket usage  
  
- Bracket termination rule  
  
- Alternate Code Set Allowed indicator  
  
- Normal-flow send/receive mode  
  
  The next three tables list the FM Profile 3 options that [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] supports. Host Integration Server rejects any BIND option that specifies an option value not listed in these tables.  
  
### Supported options for BIND requests from primary LUs  
  
|Usage option|Value|Meaning|  
|------------------|-----------|-------------|  
|Chaining use element|0|Can send only single-element chains|  
||1|Can send single- or multiple-chains|  
|Request control mode|0|Immediate request mode used|  
|Chain response protocol|01|Can request only exception-only responses|  
||10|Can request only definite responses|  
||11|Can request definite or exception-only responses|  
|Compression indicator|0|Cannot send compressed data|  
||1|Can send compressed data (LU 1 only)|  
|Send EB indicator|1|Can send an end bracket|  
  
### Supported options for BIND requests from secondary LUs  
  
|Usage option|Value|Meaning|  
|------------------|-----------|-------------|  
|Chaining use element|0|Can only send single-element chains (not LU 2)|  
||1|Can send single- or multiple-chains|  
|Request control mode|0|Immediate request mode used|  
|Chain response protocol|01|Can request only exception-only responses|  
||10|Can request only definite responses|  
||11|Can request definite or exception-only responses|  
|Compression indicator|0|Cannot send compressed data|  
|Send EB indicator|1|Cannot send end bracket|  
  
### Supported common protocol values for BIND requests from any LU  
  
|Usage option|Value|Meaning|  
|------------------|-----------|-------------|  
|FM header usage|0|Cannot exchange FM headers|  
||1|Can exchange FM headers|  
|Bracket usage|1|Bracket protocols must be used|  
|Bracket termination rule|1|Bracket termination rule 1 is used|  
|Alternate code set allowed|0|Must use Extended Binary Coded Decimal Interchange Code (EBCDIC)|  
|Normal flow send/receive mode|10|Half-duplex flip-flop|  
  
## See Also  
 [Transmission Service and Function Management Profiles](../core/transmission-service-and-function-management-profiles1.md)