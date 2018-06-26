---
title: "TS Profile 31 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f3ff9c0f-ce59-4bc6-b8b8-27022b1799d5
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# TS Profile 3
Transmission service (TS) Profile 3 is supported on primary logical unit-secondary logical unit (PLU-SLU) sessions using LU types 0, 1, 2, or 3. Selection is a BIND option. This profile specifies the following session rules:  
  
- PLU-SLU and SLU-PLU normal flows are paced.  
  
- Sequence numbers are used on the normal flows.  
  
- BIND, UNBIND, CLEAR, and SDT are supported.  
  
  The TS usage subfields defining the options for this profile are the following:  
  
- Pacing counts  
  
- Maximum request/response (RU) sizes on the normal flows  
  
## See Also  
 [Transmission Service and Function Management Profiles](../core/transmission-service-and-function-management-profiles1.md)