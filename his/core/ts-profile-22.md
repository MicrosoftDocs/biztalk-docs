---
description: "Learn more about: TS Profile 2"
title: "TS Profile 22"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
