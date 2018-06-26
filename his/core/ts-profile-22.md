---
title: "TS Profile 22 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 51e8c91e-3d67-438a-8515-417f5633bcf6
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# TS Profile 2
Transmission service (TS) Profile 2 is supported on primary logical unit-secondary logical unit (PLU-SLU) sessions using LU 0. This profile specifies the following session rules:  
  
- Primary logical unit-secondary logical unit (PLU-SLU) and SLU-PLU normal flows are paced.  
  
- Sequence numbers are used on the normal flows whenever the transmission header (TH) format used includes a sequence number field.  
  
- CLEAR is supported.  
  
- SDT, RQR, STSN, and CRV are not supported.  
  
  The TS usage subfields defining the options for this profile are the following:  
  
- Pacing window counts  
  
- Maximum request/response (RU) sizes on the normal flows  
  
## See Also  
 [Transmission Service and Function Management Profiles](../core/transmission-service-and-function-management-profiles1.md)