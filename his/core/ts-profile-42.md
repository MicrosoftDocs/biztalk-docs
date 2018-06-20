---
title: "TS Profile 42 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2c6928ff-c199-4f7f-839b-c69d1015fe18
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# TS Profile 4
Transmission service (TS) Profile 4 is supported on logical unit-logical unit (LU-LU) sessions using LU types 0 or 1. This profile specifies the following session rules:  
  
- Primary logical unit-secondary logical unit (PLU-SLU) and SLU-PLU normal flows are paced.  
  
- Sequence numbers are used on the normal flows whenever the transmission header (TH) format used includes a sequence number field.  
  
- SDT, CLEAR, RQR, and STSN are supported.  
  
- CRV is supported when session-level cryptography is selected via a BIND parameter.  
  
  The TS usage subfields defining the options for this profile are the following:  
  
- Pacing window counts  
  
- Maximum request/response (RU) sizes on the normal flows  
  
## See Also  
 [Transmission Service and Function Management Profiles](../core/transmission-service-and-function-management-profiles1.md)